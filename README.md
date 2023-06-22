# react-native-cazh-datecs-printer

It only **works on Android**.

## As I made this project with a very short deadline, it's specific for the app that I was working on and it might not be suitable for you, although fell free to fork and modify it.

#### Breaking Changes [RN v0.47.2](https://github.com/facebook/react-native/releases/tag/v0.47.2)

Remove unused createJSModules calls.

- if on RN < 0.47.2 `npm i react-native-cazh-datecs-printer@0.1.1`
- if on RN > 0.47.2 `npm i react-native-cazh-datecs-printer`

### Printer used for tests

DPP 250

---

## Getting started (latest version)

`$ npm install react-native-cazh-datecs-printer --save`

### Mostly automatic installation

`$ react-native link react-native-cazh-datecs-printer`

### Add permissions in your AndroidManifest.xml

```
<uses-permission android:name="android.permission.BLUETOOTH"/>
<uses-permission android:name="android.permission.BLUETOOTH_ADMIN"/>
```

### Manual installation

#### Android

1. Open up `android/app/src/main/java/[...]/MainActivity.java`

- Add `import com.renancsoares.datecsprinter.RNDatecsPrinterPackage;` to the imports at the top of the file
- Add `new RNDatecsPrinterPackage()` to the list returned by the `getPackages()` method

2. Append the following lines to `android/settings.gradle`:
   ```
   include ':react-native-cazh-datecs-printer'
   project(':react-native-cazh-datecs-printer').projectDir = new File(rootProject.projectDir, 	'../node_modules/react-native-cazh-datecs-printer/android')
   ```
3. Insert the following lines inside the dependencies block in `android/app/build.gradle`:
   ```
     compile project(':react-native-cazh-datecs-printer')
   ```

### Examples of methods in your application.

**It's also provided in the application example**

```
connect(){
	DatecsPrinter.connect()
	.then( res => {
		// return CONNECTED
		console.log(res);
	})
	.catch( err => {
		console.log(err)
	})
}

print(text){
	DatecsPrinter.printText(text)
	.then( res => {
		// return PRINTED
		console.log(res);
	})
	.catch( err => {
		console.log(err);
	})
}

printSelfTest(){
	DatecsPrinter.printSelfTest()
	.then( res => {
		// return SELF_TEST_PRINTED
		console.log(res)
	})
	.catch( err => {
		console.log(err);
	});
}

getStatus(){
	DatecsPrinter.getStatus()
	.then( res => {
		// If everything is OK, it'll return 0
		// you can use this before printing to make sure that nothing wrong happens
		console.log(res);
	})
	.catch( err => {
		console.log(err)
	})
}

disconnect(){
	DatecsPrinter.disconnect()
	.then( res => {
		// return DISCONNECTED
		console.log(res);
	})
	.catch( err => {
		console.log(err);
	})
}
```

### Tags definition

- `{reset}` Reset to default settings.
- `{br}` Line break. Equivalent of new line.
- `{b}, {/b}` Set or clear bold font style.
- `{u}, {/u}` Set or clear underline font style.
- `{i}, {/i}` Set or clear italic font style.
- `{s}, {/s}` Set or clear small font style.
- `{h}, {/h}` Set or clear high font style.
- `{w}, {/w}` Set or clear wide font style.
- `{left}` Aligns text to the left paper edge.
- `{center}` Aligns text to the center of paper.
- `{right}` Aligns text to the right paper edge.
