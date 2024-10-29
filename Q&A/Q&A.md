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

### Q2: How to arrange value in ExposedDropdownMenu in Android Compose?
To arrange the text for each item in `ExposedDropdownMenu` (i.e. `ExposedDropdownMenuItem` at material3), one just have to arrange the text as arrange `Text` component in `text` argument of `ExposedDropdownMenuItem`)

For example, source code from chatGPT.

```
import androidx.compose.foundation.layout.fillMaxWidth
import androidx.compose.material3.*
import androidx.compose.runtime.*
import androidx.compose.ui.Alignment
import androidx.compose.ui.Modifier
import androidx.compose.ui.text.style.TextAlign
import androidx.compose.ui.unit.dp
import androidx.compose.ui.unit.sp

@OptIn(ExperimentalMaterial3Api::class)
@Composable
fun CustomExposedDropdownMenu() {
    var expanded by remember { mutableStateOf(false) }
    var selectedOption by remember { mutableStateOf("") }
    val options = listOf("Option 1", "Option 2", "Option 3")

    ExposedDropdownMenuBox(expanded = expanded, onExpandedChange = { expanded = !expanded }) {
        TextField(
            value = selectedOption,
            onValueChange = { /* no-op */ },
            readOnly = true,
            label = { Text("Select an option") },
            trailingIcon = {
                Icon(Icons.Default.ArrowDropDown, contentDescription = null)
            },
            modifier = Modifier.fillMaxWidth()
        )

        ExposedDropdownMenu(
            expanded = expanded,
            onDismissRequest = { expanded = false },
            modifier = Modifier.fillMaxWidth()
        ) {
            options.forEach { option ->
                DropdownMenuItem(
                    text = {
                        Text(
                            text = option,
                            textAlign = TextAlign.Start,
                            fontSize = 16.sp
                        )
                    },
                    onClick = {
                        selectedOption = option
                        expanded = false
                    }
                )
            }
        }
    }
}
```

For answer from chatGPT, see this [article](https://github.com/40843245/Android-Compose/blob/main/Q%26A/How%20to%20arrange%20value%20in%20ExposedDropdownMenu%20in%20Android%20Compose.md).
