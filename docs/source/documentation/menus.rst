Menu Bar
========

DPG містить до двох типів панелей меню

Viewport Menu Bar 
    Приєднано до області перегляду

Menu Bar
   Прикріплено до вказаного вікна

За винятком того, що вони прив'язані до різних батьків, вони обидва діють однаково.

Типовий рядок меню складається з наступних компонентів:

Menu Bar:
    Стрічка головного меню. Використовується для розміщення меню.
Menu:
    Спливаючі вікна, які використовуються для відображення елементів у розбірному вигляді.
Menu Item:
    Елементи, які можуть запускати зворотні виклики та відображати галочку.

----- Використання -----

Елементи, додані до рядка меню, відображаються зліва направо. 
Елементи, додані до меню, відображаються зверху вниз.

Меню можуть бути вкладені в інші меню.

Будь-який віджет можна додати до меню.

**Приклад панелі меню у вікні перегляду** 

.. code-block:: python

    import dearpygui.dearpygui as dpg

    def print_me(sender):
        print(f"Menu Item: {sender}")

    dpg.create_context()
    dpg.create_viewport(title='Custom Title', width=600, height=200)

    with dpg.viewport_menu_bar():
        with dpg.menu(label="File"):
            dpg.add_menu_item(label="Save", callback=print_me)
            dpg.add_menu_item(label="Save As", callback=print_me)

            with dpg.menu(label="Settings"):
                dpg.add_menu_item(label="Setting 1", callback=print_me, check=True)
                dpg.add_menu_item(label="Setting 2", callback=print_me)

        dpg.add_menu_item(label="Help", callback=print_me)

        with dpg.menu(label="Widget Items"):
            dpg.add_checkbox(label="Pick Me", callback=print_me)
            dpg.add_button(label="Press Me", callback=print_me)
            dpg.add_color_picker(label="Color Me", callback=print_me)

    dpg.setup_dearpygui()
    dpg.show_viewport()
    dpg.start_dearpygui()
    dpg.destroy_context()

**Menu Bar Example**

.. code-block:: python

    import dearpygui.dearpygui as dpg

    dpg.create_context()

    dpg.create_viewport(title='Custom Title', width=600, height=200)

    def print_me(sender):
        print(f"Menu Item: {sender}")

    with dpg.window(label="Tutorial"):
        with dpg.menu_bar():
            with dpg.menu(label="File"):
                dpg.add_menu_item(label="Save", callback=print_me)
                dpg.add_menu_item(label="Save As", callback=print_me)

                with dpg.menu(label="Settings"):
                    dpg.add_menu_item(label="Setting 1", callback=print_me, check=True)
                    dpg.add_menu_item(label="Setting 2", callback=print_me)

            dpg.add_menu_item(label="Help", callback=print_me)

            with dpg.menu(label="Widget Items"):
                dpg.add_checkbox(label="Pick Me", callback=print_me)
                dpg.add_button(label="Press Me", callback=print_me)
                dpg.add_color_picker(label="Color Me", callback=print_me)

    dpg.setup_dearpygui()
    dpg.show_viewport()
    dpg.start_dearpygui()
    dpg.destroy_context()

**Results**

.. image:: https://raw.githubusercontent.com/hoffstadt/DearPyGui/assets/wiki_images/menus.PNG
