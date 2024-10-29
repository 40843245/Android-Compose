# Android Compose
## Q&A
### Q1: How to arrange value in OutlinedTextField in Android Compose?
In `OutlineTextField`, set the `textStyle` argument as following code snippets.

```
textStyle = LocalTextStyle.current.copy(
            fontSize = 18.sp,
            textAlign = TextAlign.Start // You can use TextAlign.Center or TextAlign.End
        )
```

For example, source code from chatGPT.

```
import androidx.compose.foundation.layout.fillMaxWidth
import androidx.compose.material3.OutlinedTextField
import androidx.compose.material3.Text
import androidx.compose.runtime.Composable
import androidx.compose.runtime.remember
import androidx.compose.runtime.mutableStateOf
import androidx.compose.runtime.getValue
import androidx.compose.runtime.setValue
import androidx.compose.ui.Alignment
import androidx.compose.ui.Modifier
import androidx.compose.ui.graphics.Color
import androidx.compose.ui.text.input.TextFieldValue
import androidx.compose.ui.text.style.TextAlign
import androidx.compose.ui.unit.dp
import androidx.compose.ui.unit.sp

@Composable
fun CustomOutlinedTextField() {
    var text by remember { mutableStateOf(TextFieldValue("")) }

    OutlinedTextField(
        value = text,
        onValueChange = { text = it },
        modifier = Modifier.fillMaxWidth(),
        textStyle = LocalTextStyle.current.copy(
            fontSize = 18.sp,
            textAlign = TextAlign.Start // You can use TextAlign.Center or TextAlign.End
        ),
        placeholder = { Text("Enter text here") },
        colors = TextFieldDefaults.outlinedTextFieldColors(
            focusedContainerColor = Color.Transparent,
            unfocusedContainerColor = Color.Transparent
        )
    )
}

```

For answer from chatGPT, see this [article](https://github.com/40843245/Android-Compose/blob/main/Q%26A/How%20to%20arrange%20value%20in%20OutlinedTextField%20in%20Android%20Compose%3F.md)

### Q2: How to align Text in ExposedDropdownMenuItem in Android Compose?
To arrange the text for each item in `ExposedDropdownMenu` (i.e. `ExposedDropdownMenuItem` at material3), one have to add a `Box` component under each `ExposedDropdownMenuItem` component, setting the alignment and arrangement of `Box`, lastly, put the `Text` in the `Box`. (Originally, `Text` is directly child of `ExposedDropdownMenuItem`)

For example, source code from chatGPT.

```@Composable
fun AlignedDropdownMenu() {
    val items = listOf("Orange", "Apple", "Banana", "Grape")
    var selectedItem by remember { mutableStateOf("") }
    var expanded by remember { mutableStateOf(false) }

    ExposedDropdownMenuBox(
        expanded = expanded,
        onExpandedChange = { expanded = !expanded }
    ) {
        OutlinedTextField(
            value = selectedItem,
            onValueChange = { selectedItem = it },
            label = { Text("Select Fruit") },
            trailingIcon = {
                Icon(
                    imageVector = if (expanded) Icons.Filled.ArrowDropUp else Icons.Filled.ArrowDropDown,
                    contentDescription = null
                )
            },
            modifier = Modifier.menuAnchor()
        )

        ExposedDropdownMenu(
            expanded = expanded,
            onDismissRequest = { expanded = false }
        ) {
            items.forEach { item ->
                DropdownMenuItem(
                    onClick = {
                        selectedItem = item
                        expanded = false
                    }
                ) {
                    // Center-align the text
                    Box(
                        modifier = Modifier.fillMaxWidth(),
                        contentAlignment = Alignment.Center
                    ) {
                        Text(text = item)
                    }
                }
            }
        }
    }
}
```

For answer from chatGPT, see this [article]([https://github.com/40843245/Android-Compose/blob/main/Q%26A/How%20to%20arrange%20value%20in%20ExposedDropdownMenu%20in%20Android%20Compose.md](https://github.com/40843245/Android-Compose/blob/main/Q&A/How%20to%20align%20Text%20in%20ExposedDropdownMenuItem%20in%20Android%20Compose.md)).
