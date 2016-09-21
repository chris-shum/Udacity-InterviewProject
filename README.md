# Udacity-InterviewProject

Question 1 - What’s your favorite tool or library for Android? Why is it so useful?

- My favorite library for Android currently is Retrofit with jsonschema2pojo.  A manual API call in Android requires creating a new thread generally with an AsyncTask, and then creating a ton of JSONObjects or JSONArrays depending on the incoming data.  jsonschema2pojo takes the JSON data and automatically creates POJOs (Plain Old Java Objects) for you to use. Retrofit takes care of the call and creates a separate thread for you.  It's so much simpler to implement and the number of lines of code is reduce immensely.

Question 2 - You want to open a map app from an app that you’re building. The address, city, state, and ZIP code are provided by the user. What steps are involved in sending that data to a map app?

- In order to get data from a user, you'll first need some edittexts in your app and probably a button of sorts to commence the data grab (edittext.getString()).  Once the app has the address, you'll have a few options.  A simple way would be to create a textview with the address.  The textview would need the attribute android:autoLink="map" in the XML.  This attribute would make the textview clickable and automatically open Google Maps and search the address for you.  Another way would taking the address and passing it through and implicit intent.  The implicit intent would ask what application you'd like to open/use the data being passed through it with.  In this case, most likely Google Maps as well.

Question 3 - Implement a method to perform basic string compression using the counts of repeated characters. For example, the string aabcccccaaa would become a2b1c5a3. If the "compressed" string would not become smaller than the original string, your method should return the original string. The method signature is: “public static String compress(String input)” You must write all code in proper Java, and please include import statements for any libraries you use.
```
public class Udacity {
    public static void main(String[] args) {
        Scanner reader = new Scanner(System.in);
        System.out.println("Please enter string:");
        String inputString = reader.nextLine();

//        System.out.println(compress("aabcccccaaa"));
        System.out.println(compress(inputString));
    }

    public static String compress(String input) {
        String output = "";
        int count = 0;
        for (int i = 0; i < input.length() - 1; i++) {
            count++;
            if (input.charAt(i) != input.charAt(i + 1)) {
                output = output + input.charAt(i) + count;
                count = 0;
            } else {
                String newString = "";
                for (int j = 1; j < input.length(); j++) {
                    newString = newString + input.charAt(j);
                }
                compress(newString);
            }
        }
        output = output + input.charAt(input.length() - 1) + (count + 1);
        if (output.length() >= input.length()) {
            return input;
        }
        return output;
    }
}
```
Question 4 - List and explain the differences between four different options you have for saving data while making an Android app. Pick one, and explain (without code) how you would implement it.

- Four ways that I can think of to save data in an Android app are SharedPreferences, SaveInstanceState, SQLite database, an external third party library database like Realm or Firebase.  Personally I prefer external databases.  SharedPreferences and SaveInstanceStates I feel are meant to save smaller things like primitives.  Although I have used them to save objects, I feel they're not meant to be used that way.  SharedPreferences for instance, meant to save say a setting preference on an app.  SaveInstanceState used mainly to save an activity's state as a backup; for example if the activity is destroyed suddenly like with screen rotation.  SQLite is great, but I feel creating a DBHelper to make calls or write into it becomes a pain.  Also the SQLite syntax is white space sensitive.  You could accidentally have an extra space in a call and spend a lot of time trying to find that error.  External libraries simplify saving with a few methods.  Also they're designed to hold objects if needed.

Question 5 - What are your thoughts about Fragments? Do you like or hate them? Why?

- I am not a fan of fragments.  Unless I'm using something like a TabLayout and ViewPager or a Master/Detail view, I see no reason to use them.  It's an extra 2 files to keep track of (XML and java fragment), I need methods to attach them to the appropriate activity, I need to create a reference to the context of the activity containing the fragment for a number of things, and passing data between them is a bit more complicated than it is with just intents.  Yes, swapping fragments in an activity is nice, but switching between activities accomplishes the nearly same thing.  It just feels like a lot more extra work for not that much more benefit.

Question 6 - If you were to start your Android position today, what would be your goals a year from now?

- I just want to be a stronger developer.  It's simple to create your own apps and brute force through things.  I want to learn the best practices; strengthen my understanding of coding design patterns like MVP, understand creating clean code with good performance and use of resources in mind.  I want to be able to pair program with experienced developers.  I want to be able to look at already developed code, understand it completely and be able to improve it and/or add on to it.

- I also want to be able to good enough to transfer my Android experience/knowledge into other coding languages.  Whether it's expand my mobile development skills into say iOS, or reach over to web development, machine learning, etc. 
