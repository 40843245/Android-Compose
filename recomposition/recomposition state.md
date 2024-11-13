# recomposition state
## category
<img width="530" alt="image" src="https://github.com/user-attachments/assets/e77f0628-288a-421f-a36a-72ba973d232d">

For more details, see 4:13 of `Debugging Jetpack Compose` (official video)[^1]

## mark an interface recomposition state
### @Stable
To mark an interface recomposition state as stable, use `@Stable` annotation.

#### example
From `Lifecycle of composables (official docs)`[^2]
```
// Marking the type as stable to favor skipping and smart recompositions.
@Stable
interface UiState<T : Result<T>> {
    val value: T?
    val exception: Throwable?

    val hasError: Boolean
        get() = exception != null
}
```

## reference
[^1]: [`Debugging Jetpack Compose` (official video)](https://www.youtube.com/watch?v=Kp-aiSU8qCU)

[^2]: [`Lifecycle of composables (official docs)`](https://developer.android.com/develop/ui/compose/lifecycle)
