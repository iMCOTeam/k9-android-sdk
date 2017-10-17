Usage
-----

In order to use the library:

** Gradle dependency** 

  -  Add the following to your project level `build.gradle`:
 
```gradle
allprojects {
	repositories {
		maven { url "https://raw.github.com/iMCOTeam/k9-android-sdk/master" }
	}
}
```
  -  Add this to your app `build.gradle`:
 
```gradle
dependencies {
	compile 'com.imco.android:k9-android-sdk:2.１.１'
}
```
Get Started
-----
* Init  SDK in your Application
```
CommandManager.init(Context context);
```

* All Connect command in ConnectManager.java.eg :
```
ConnectManager.getInstance().connect(Mac_address);
```
*The response of all  Connect command  in ConnectCallback.java, you need implement it , eg : 
```
 private ConnectCallback mCallback = new ConnectCallback() {
        @Override
        public void foundDevices(BluetoothDevice device, int rssi, byte[] scanRecord) {
        	// do something, eg: connect th band
         }
         @Override
        public void connectStatus(boolean succeeded, int code) {
     		// do something
        }
    };
```	
Register :
```
ConnectManager.getInstance().registerCallback(mCallback);
```
* All the commands that interact with the band are in the CommandManager.java; eg:
```
	// Get the name of the current band
        CommandManager.getDeviceName(new SendCommandCallback() {
            @Override
            public void onCommandSend(boolean status) {
		//  status is ture : the command was sent successfully
		//  status is false : the command was sent failed
            }

            @Override
            public void onDisconnected() {
                // The bend is not connected
            }

            @Override
            public void onError(Throwable error) {
                // some error
            }
        });
    }
```
* The response of all interactive commands in CommandCallback.java. you need implement some method for you need,eg:
```
 CommandCallback mCallback = new CommandCallback() {
            @Override
            public void onNameRead(String data) {
		// data is the name of the current band
            }
```
Register :
```
CommandManager.registerCallback(mCallback);
```

DEMO
-----
[k9-android-demo](https://github.com/iMCOTeam/k9-android-demo) 
