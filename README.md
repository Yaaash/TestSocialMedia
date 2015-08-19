# TestSocialMedia

This app tests all the social media linkage to one app and the maximum, regress usage of tools.


Facebook Integeration 

Step 1: Add depedencies in Project (build.gradle -app)
	        repositories { mavenCentral() }
	        compile 'com.facebook.android:facebook-android-sdk:4.0.0'

Step 2: Add your package and main activity details in Facebook Developer section (create facebook developer account if you dont have one)

Step 3: create Key Hash - beacause - To authenticate the exchange of information between your app and the Facebook, you need to generate a release key hash and add this to the Android settings within your Facebook App ID. 
	      Without this, your Facebook integration may not work properly when you release your app to the store.

	     can be generated using two methods
	
	     a) Java code - add in main activity OnCreate Method
	      // Add code to print out the key hash
         try {
             PackageInfo info = getPackageManager().getPackageInfo(
                    "com.facebook.samples.hellofacebook",
                    PackageManager.GET_SIGNATURES);
             for (Signature signature : info.signatures) {
                MessageDigest md = MessageDigest.getInstance("SHA");
                md.update(signature.toByteArray());
                Log.d("KeyHash:", Base64.encodeToString(md.digest(), Base64.DEFAULT));
             }
         } catch (PackageManager.NameNotFoundException e) {

         } catch (NoSuchAlgorithmException e) {

         }

    	b) Android Studio Terminal
	    Android cannot located jdk and jre in terminal so locate the following files in your c:/ First openssl (you may have to download it) and Second keytool - it is located in Java folder
	    The demo terminal command to be used-
	    "C:\Program Files\Java\jre7\bin\keytool.exe" -exportcert -alias sandroiddebugkey -keystore C:\Users\yashika\.android\debug.keystore | "C:\Users\yashika\Downloads\openssl-0.9.8k_WIN32\bin\openssl.exe" sha1 -binary | "C:\Users\yashika\Downloads\openssl-0.9.8k_WIN32\bin\openssl.exe" base64
	

Step 4: Start using Facebook events

Step 5: Add Application ID given to you in Developer options in your strings.xml

Step 6: Add User Permissions and Facebook meta data in manifest.xml

Step 7: If using Facebook Login and Share feature - one more activity is supposed to be added to manifest.xml - "FacebookActivity"

Step 8: If want to send Images and Videos using your app. Then you also need to declare FacebookContentProvider in you manifest. Naming convention based on your Application ID
	Append your app id to the end of the authorities value. For example if your Facebook app id is 1234, the declaration looks like:
	<provider android:authorities="com.facebook.app.FacebookContentProvider1234"
          android:name="com.facebook.FacebookContentProvider"
          android:exported="true" />

Now you have all the prerequisites ready for Login Page integration in Facebook ->

Step 9: Inititalise facebook sdk in yor code.

Step 10: Now you can use different facebook functionalitites. 
		// check sample project for more.
