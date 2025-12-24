# Installing Flet Module
```bash
pip install flet
```

# Basic Flet Structure
A very minimal Flet app has the following structure:
```python
import flet as ft

def main(page: ft.Page):
	pass

ft.app(target=main)
```
A typical Flet program ends with a call to `flet.app()` where the app starts waiting for new user sessions. Function `main()` is an entry point in a Flet application. It's being called on a new thread for every user session with a `Page` instance passed into it. When running Flet app in the browser a new user session is started for every opened tab or page. When running as a desktop app there is only one session created.

`Page` is like a "canvas" specific to a user, a visual state of a user session. To build an application UI you add and remove controls to a page, update their properties. Code sample above will be displaying just a blank page to every user.

To view the Flet app in web browser,
```python
ft.app(target=main, view=ft.WEB_BROWSER)
```
# Controls
User interface is made of **Controls** (aka widgets). To make controls visible to a user they must be added to a `Page` or inside other controls. Page is the top-most control. Nesting controls into each other could be represented as a tree with Page as a root.

Controls are just regular Python classes. Create control instances via constructors with parameters matching their properties, for example:
```python
t = ft.Text(value="Hello, world!", color="green")
```
To display control on a page add it to `controls` list of a Page and call `page.update()` to send page changes to a browser or desktop client:
```python
import flet as ft

def main(page: ft.Page):
	t = ft.Text(value="Hello, world!", color="green")
	page.controls.append(t)
	page.update()
	
ft.app(target=main)
```

You can modify control properties and the UI will be updated on the next `page.update()`:
```python
t = ft.Text()
page.add(t)

for i in range(10):
	t.value = f"Step {i}"
	page.update()
	time.sleep(1)
```
- Here `page.add()` is a shortcut for `page.controls.append(t)` and then `page.update()`

Some controls are "container" controls (like Page) which could contain other controls. For example, `Row` control allows arranging other controls in a row one-by-one:
```python
page.add(
		 ft.Row(controls=[
			 ft.Text("A"),
			 ft.Text("B"),
			 ft.Text("C")
		 ])
)
```
or `TextField` and `ElevatedButton` next to it:
```python
page.add(
		 ft.Row(controls=[
			 ft.TextField(label="Your name"),
			 ft.ElevatedButton(text="Say my name!")
		 ])
)
```
`page.update()` is smart enough to send only the changes made since its last call