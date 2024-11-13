# debugging with trace
## category
<img width="507" alt="image" src="https://github.com/user-attachments/assets/3f47c51f-941c-4614-aa16-fc4157b2045f">

### system trace
#### use system trace for Android Compose
Now, one can use system trace for android compose by following step.

1. add dependency through project structure.

```
androidx.compose.runtime:runtime-tracing:<version>
```

> [!WARNING]
> DON'T forget to sync after adding depedencies.

As shown in following figure.

<img width="794" alt="image" src="https://github.com/user-attachments/assets/da53eae3-15b1-4ecf-8dea-5ecc4b1a2d6e">

2. In Android Studio, open Profiler.

3. Click on CPU lane.

4. choose `system trace` option.

5. And click record button to record the CPU lane etc.

6. Now, you can use your app and see the info of system trace.

7. After that, you can analyze the suspicious reason through info of system trace you just got.

##### demo
For demo, see [17:32 in `Debugging Jetpack Compose`](https://www.youtube.com/watch?v=Kp-aiSU8qCU)
