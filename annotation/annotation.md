# annotation
## `@Stable`
`@Stable` annotation will mark the object is in a `Stable` state so that in Compose compiler, this object might change, but when it changes, Compose runtime will be notified.

## `@Immutable`
`@Immutable` annotation will mark the object is `Immutable`. Thus, this object is immutable for optimization in Android Compose. With this annotation, there are no unnecessary recomposition at runtime. Otherwise, there may be unncessary recomposition at runtime.

> [!TIP]
> There are 2 ways to make it stable again, which are using @Stable and @Immutable.
>
> Using `@Stable`, as mentioned above, it means that the value can be changed, but when it does change, we have to notify Compose compiler. The way to do it is through using `mutableStateOf()`.
>
> As following example
>
> ```
> @Stable
> class SomeViewState {
> var isLoading by mutableStateOf(false)
> }
> ```
>
> Using `@Immutable`, it means that you will always make a new copy of the data when you pass into the Composable, in other wards, you make a promise that your data is immutable.
>
> From the example above.
>
> ```
> @Immutable
> data class SomeViewState {
>   val list: List<String>
> }
>
> @Composable
> fun ShowSomething(data: SomeViewState) {
> }
>
> After annotating with `@Immutable`, you should make sure to make a new list instead of mutating your list directly. Using following code snippets.
>
> ```
> class ViewModel {
>   val state: SomeViewState = SomeViewState(listOf())
>   fun removeLastItem() {
>       val newList = state.list.toMutableList().apply {
>               removeLast()
>           }
>       state = state.copy(list = newList)
>   }
> }
>
> Please **DON'T**
>
> ```
> class ViewModel {
>   val state: SomeViewState = SomeViewState(mutableListOf())
>   fun removeLastItem() {
>       state.list.removeLast() // <=== you violate your promise of @Immutable!
>   }
> }
> ```
