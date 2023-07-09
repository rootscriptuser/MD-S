# Python library Rich

# Help && Inspect
```python
import rich
from rich import inspect

inspect(rich)
print(help(rich))
```
## Progress bar example
```python
from rich.progress import track
from time import sleep

def process_data():
    sleep(0.02)


for _ in track(range(100), description='[green]Processing data'):
    process_data()
```

# Console like status in loop
```python
from rich.console import Console
from time import sleep

console = Console()

data = [1, 2, 3, 4, 5]
with console.status("[bold green]Fetching data...") as status:
    while data:
        num = data.pop(0)
        sleep(1)
        console.log(f"[green]Finish fetching data[/green] {num}")

    console.log(f'[bold][red]Done!')
```

# Tree like output of info
```python
from rich.tree import Tree
from rich import print as rprint


tree = Tree("Family Tree")
tree.add("Mom")
tree.add("Dad")
tree.add("Brother").add("Wife")
tree.add("[red]Sister").add("[green]Husband").add("[blue]Son")

rprint(tree)
```
# Tables 
```python
from rich.console import Console
from rich.table import Table

table = Table(title="Todo List")

table.add_column("S. No.", style="cyan", no_wrap=True)
table.add_column("Task", style="magenta")
table.add_column("Status", justify="right", style="green")

table.add_row("1", "Buy Milk", "✅")
table.add_row("2", "Buy Bread", "✅")
table.add_row("3", "Buy Jam", "❌")

console = Console()
console.print(table)
```
#Colums /w cards
```python
import json
from urllib.request import urlopen

from rich.console import Console
from rich.columns import Columns
from rich.panel import Panel


def get_content(user):
    """Extract text from user dict."""
    country = user["location"]["country"]
    name = f"{user['name']['first']} {user['name']['last']}"
    return f"[b]{name}[/b]\n[yellow]{country}"


console = Console()


users = json.loads(urlopen("https://randomuser.me/api/?results=30").read())["results"]
user_renderables = [Panel(get_content(user), expand=True) for user in users]
console.print(Columns(user_renderables))
```
# More console
```python3
from rich.console import Console
from rich.text import Text

console = Console()
console.print("Some lorem ipsum text.", style="bold underline red on white")

text = Text("Hello bello")
text.stylize("bold magenta", 8,6)
console.print(text)

console.print("Successfull", style="success")
console.print("errr", style="error")
console.print("ops [error] failed [/error]")
```

