# debugging in Jetpack Compose
## approach
There are 5 ways to debug your App in Jetpack Compose.

1. Compose debugger.
2. Layout Inspector.
3. Visual linting.
4. Composition tracing.
5. Benchmarking.
   
As shown following figure.

<img width="549" alt="image" src="https://github.com/user-attachments/assets/0f43c8bf-e2c0-4175-91c8-c2f53580173a">

### Compose debugger
See 4:00 of this video `Debugging Jetpack Compose`[^1]

### Layout Inspector
Layout Inspector can let you see preview layout without executing of your app. Of course, when you execute your app. You can use this functionality.

#### use Layout Inspector
1. define a new function or method with `@Preview` annotation. And invoke your function or methtod for UI screen.

> [!WARNING]
> The two functions or methods -- the one with `@Preview` annotation and the another one for UI screen must be place in same file.

> [!TIP]
> I suggested put two functions or methods -- the one with `@Preview` annotation and the another one for UI screen as this format in following example.

##### example with Layout Inspector

```
@Composable
fun UpdateInfoScreen(){
  // your actually UI component in UI screen.
}

@Preview(showBackground = true)
@Composable
fun PreviewUpdate() {
    UpdateInfoScreen()
}
```

##### reference
1. second page of `CH3-UiProgram` pdf file under [`黃彬華老師 Android App`](https://www.dropbox.com/scl/fo/9k2go2pqo1efyde1od48w/AH6RTHa3tG0ZnuSSMS5SImk?rlkey=y073ekayhsbagjwfo241sensf&e=1&dl=0)
   
<img width="1165" alt="image" src="https://github.com/user-attachments/assets/1949cd99-6539-4a56-adc9-1a7d8d34b54e">

2. [Preview your UI with composable previews(Android official docs)](https://developer.android.com/develop/ui/compose/tooling/previews)

### Visual Linting
See 8:03 of this video `Debugging Jetpack Compose`[^1]

### Composition tracing
In Android, `tracing` is self-explanatory, it can trace the process of tasks (the execution order of the tasks) when debugging your app.

It can be categorized into system tracing and method tracing.

For more details, see 

+ [debugging with trace.md (my note at GitHub)](https://github.com/40843245/Android-Compose/blob/main/debugging/debugging%20with%20trace.md)

+ 14:48 of `Debugging Jetpack Compose`[^1]


###  Benchmarking
See 5:29 of `Debugging Jetpack Compose`[^1]

[^1]: [Debugging Jetpack Compose](https://www.youtube.com/watch?v=Kp-aiSU8qCU)

