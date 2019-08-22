# GUI Bedos

PySide widgets and helpers

This project is used alongside [Qt.py](https://github.com/mottosso/Qt.py).

If you don't plan on using Qt.py, you must comply with the Qt5/PySide2 syntax (`from Qt import QtWidgets`) 

# CSS

It is common to apply a custom CSS stylesheet to a QApplication.

This modules allows to load 6 different themes, borrowed from the FreeCAD project

Stylesheets and icons are provided

Available themes are

- `dark-blue`
- `dark-green`
- `dark-orange`
- `light-blue`
- `light-green`
- `light-orange`

````python
from Qt.QtWidgets import QApplication, QPushButton
from guibedos import css

app = QApplication([])
css.set_theme(app, 'dark-blue')

button = QPushButton('Hello you')
button.show()

app.exec_()
````

<-- put a capture of themes here -->

# widgets

## FlowLayout

The "flow" layout is not available in Qt.

Allows to layout in 2D a 1D array of widgets

````python
from Qt.QtWidgets import QPushButton
from guibedos.widgets import FlowLayout

layout = FlowLayout()
layout.addWidget(QPushButton('one'))
layout.addWidget(QPushButton('two'))
layout.addWidget(QPushButton('three'))
layout.addWidget(QPushButton('four'))
````

<-- put a gif of the widget here -->

## TagBar

An augmented QLineEdit with buttons, allowing to edit a list of "tags"

<-- put a gif of the widget here -->

## DeclarativeForm

The `DeclarativeForm` allows to generate widgets from a data structure of properties

Useful for asking the user a series of info without the hassle of manually creating the widgets

<-- put an image of the widget here -->

````python
from guibedos import declarative_form as df

property_ = df.Group('personal_info', caption="Personnal Information", properties=(
    df.Text('name', caption='Name', default='Jean'),
    df.Text('surname', caption='Surname', default='Bauchefort'),
    df.Text('password', caption='Password')
))
````

Calling `data()` on the widget returns a data structure reflecting property's structure, filled with user-entered values

````json
{
 "personal_info": {
  "name": "Jean",
  "surname": "Bauchefort",
  "password": ""
 }
}
````

### helpers

#### Update Combo

Updates a QComboBox items and tries to select previously selected item

If previously selected item was present, no QSignal is emitted

````python
import guibedos.helpers

guibedos.helpers.update_combo(some_qcombobox, ['some', 'items'])
````

## Notes

- CSS stylesheets and icons are borrowed from FreeCAD, more info 
[here](https://github.com/FreeCAD/FreeCAD/tree/master/src/Gui/Stylesheets)

- Some parts of this project are borrowed from GPLv2 licensed projects. If so, it is stated in the file
