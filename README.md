# constructor-ko-android-ma-kha-use-kiya-jata-han
1. Custom Views
Jab aap custom views banate hain, to aapko constructors ka use karna padta hai taaki aapka view sahi tarike se initialize ho. Android me custom views ke liye aapko ek ya ek se zyada constructors implement karne padte hain.
Example:
class MyCustomView @JvmOverloads constructor(
    context: Context,
    attrs: AttributeSet? = null,
    defStyleAttr: Int = 0
) : View(context, attrs, defStyleAttr) {

    init {
        // Custom initialization code here
    }
}
Yahan MyCustomView class ke primary constructor me Context, AttributeSet, aur defStyleAttr parameters hain. init block me aap initialization code likh sakte hain.
2. Activities and Fragments
   Although activities and fragments generally apne default constructors ka use karte hain, kabhi-kabhi aapko custom initialization ke liye secondary constructors ki zarurat pad sakti hai.
   Example (Fragment with secondary constructor):
   class MyFragment : Fragment {
    
    constructor() : super()

    constructor(someParameter: String) : super() {
        // Use someParameter for initialization
    }

    // Rest of the fragment code
}
3.Data Classes
Data classes Android me bohot common hain, especially jab aapko kisi data model ko represent karna ho (e.g., data fetched from a server). Data classes ke primary constructor ka use hota hai properties ko initialize karne ke liye.

Example:

kotlin
Copy code
data class User(val name: String, val age: Int)
Yahan, User data class ke primary constructor me name aur age properties ko initialize kiya gaya hai.

4. Dependency Injection (e.g., with Dagger or Hilt)
Android me dependency injection frameworks (like Dagger or Hilt) ka use karte waqt constructors ka important role hota hai. Yeh frameworks constructors ka use karte hain dependencies ko inject karne ke liye.

Example with Hilt:

kotlin
Copy code
@AndroidEntryPoint
class MyActivity : AppCompatActivity() {

    @Inject
    lateinit var myDependency: MyDependency

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        // Use myDependency here
    }
}
Is example me, MyDependency class ka constructor use hota hai Hilt ke through dependency injection ke liye.
Summary
Android development me constructors ka use kai jagah hota hai:

Custom Views: Custom views ko initialize karne ke liye.
Activities and Fragments: Special initialization ke liye.
Data Classes: Data models ko represent karne ke liye.
Dependency Injection: Dependencies ko inject karne ke liye.
