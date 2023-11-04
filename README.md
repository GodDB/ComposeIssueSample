# ComposeIssueSample
this project is compose 1.5.x issue sample project 

## problum description 
1. To prevent activity recreate, the following settings were made in the manifest.
   ```
     <activity
            android:name=".MainActivity"
            android:configChanges="orientation|keyboardHidden|screenSize|locale|layoutDirection|uiMode|smallestScreenSize|screenLayout|density"
   ```
2. From compose version 1.5.0 or higher, click does not work when entering pop-up mode.
  (It works in compose version 1.4.3 and lower.)

3. video
https://github.com/GodDB/ComposeIssueSample/assets/47018460/ee71736f-63ef-4fe3-9a2f-aa35bad18040

4. code snippet
  ```
  override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContent {
            ComposeIssueSampleTheme {
                // A surface container using the 'background' color from the theme
                Surface(modifier = Modifier.fillMaxSize(), color = MaterialTheme.colorScheme.background) {

                    val context = LocalContext.current

                    Box(modifier = Modifier.fillMaxSize()) {
                        Button(
                            modifier = Modifier.align(Alignment.Center),
                            onClick = {
                                Log.e("godgod", "clicked")
                                Toast.makeText(context, "clicked!!", Toast.LENGTH_SHORT).show()
                            }
                        ) {
                            Text(text = "click!!!")
                        }
                    }
                }
            }
        }
    }
  ```
