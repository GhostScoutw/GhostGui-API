# GhostGui-API
A Minecraft GUI system to serve as an alternative to Chest and Villager GUIs.

![image](https://github.com/user-attachments/assets/28b7b87e-7036-4672-831e-5ca17fc60dd2)

# Introduction

This Datapack uses an ingame editor to create floating item displays that will serve as either empty windows, item windows or text windows, where you can edit things such as window rotation, size, color, etc.

It was made with the objective of creating a GUI system which has access to more features than similar systems, such as Chest and Villager GUIs; By giving developers the freedom of creating Menus, Settings, Custom text windows, and many more in an intuitive manner and infinitely customizable.

>[!WARNING]
>While this datapack supports multiplayer, there cannot be more than 1 player with the editor active. Always make sure that only 1 player has it active, or else the editor tools will not work as intended.


# The Editor
The editor can be activated/deactivated by executing the **toggle function**:

```mcfunction
/function ghost_gui:editor/toggle
```

With it, you will be able to create, color, move, rotate, resize, edit and delete them.

## Color Tool
![image](https://github.com/user-attachments/assets/f5f6333b-4baa-4b3e-af5d-41bbe29b658c)

By left clicking an existing window with the color tool, you will replace that window's background with glass panes of the respective color of the dye selected, which can be cycled through by right clicking.
![image](https://github.com/user-attachments/assets/a4034acd-8414-4722-baf2-d49da13b4719)


## Move Tool
![image](https://github.com/user-attachments/assets/47e8a837-1e0e-4abf-8591-7e5020978e16)

By left clicking an existing window with the move tool, you will make the selected window face your position.

![image](https://github.com/user-attachments/assets/ed31456f-c162-4c6f-8597-b67f1c05f865)

By right clicking an existing window with the move tool, you will move the selected window to your cursor position.
![image](https://github.com/user-attachments/assets/e4568d4c-e335-4182-8589-44d0e64429c2)

>[!TIP]
>Use the same key again to unselect the window.<br>Both modes can be used at the same time.


## Resize Tool
![image](https://github.com/user-attachments/assets/008ff241-4fb2-4977-8df0-fa88dbc8a019)

Left click a window to decrease its size, and right click to increase it.

![image](https://github.com/user-attachments/assets/57d40537-6479-4d17-b3e4-6a6418e01b23)


>[!NOTE]
>If you are not happy with the default sizes and resizing limits, you are able to bypass them by modifying them directly from a **load function**


## Edit Tool
![image](https://github.com/user-attachments/assets/50a67aa4-2832-4d7d-bdba-ef28ff626d1e)

## Anchor Tool
![image](https://github.com/user-attachments/assets/d6b8c59d-04ca-46ad-a24d-5da75f22d8e3)

Right click with the anchor tool to summon an **Anchor Point**, which will be the center point of your layout and serve as a reference point for the player's position. Its displayed as a bubble particle arrow on the ground. Only 1 **Anchor point** may exist at once.

Left click to delete the existing one.

![image](https://github.com/user-attachments/assets/117fa7ae-2fef-4f10-819f-778c2743a093)

>[!NOTE]
>Make sure to create the anchor point before planning out your layout, as the anchor point spawns at a fixed rotation.

## Create Tool
![image](https://github.com/user-attachments/assets/27f5a347-d509-4d79-8d1b-87fc262af83b)

The create tool has 3 different window types: **Empty**, **Item Slot** and **Text Box**, which can be cycled through by right clicking.
Left click to create the selected window type at the cursor's position.

![image](https://github.com/user-attachments/assets/4db7e50d-4931-4df7-837a-03dc6a13f58f)

## Delete Tool
![image](https://github.com/user-attachments/assets/094608ef-bc4b-4f3d-a3a7-8cec261e0078)

Right click the delete tool to cycle between deletion types, the 2 being for deleting the window entirely, and the other for deleting only its contents.
Left click to apply the deletion type to the window you are facing.

# Custom Functions

For this datapack, you can equip each window with different types of functions, such as:
- **Load**: A function that will only trigger in the moment the layout is loaded from storage
- **Tick**: A function that will trigger every tick for that window
- **Click**: A function that will trigger when any player right clicks or left clicks the window
- **Hover**: A function that will trigger when any player is directly facing the window
- **Hover_text**: A function that should contain a /data merge or /data modify for a text display's content, which will appear in the player's screen as a separate window when they are facing original window.

>[!NOTE]
>As of now, the best way of editing the functions of a window is through the mod **Axiom**, as it contains a tool that allows you to directly alter a marker's NBT data. Another method will be worked on for later versions.
>![image](https://github.com/user-attachments/assets/a489b561-1e16-4cb6-bc9c-5b0e1b0194a4)

# Saving/Loading Layouts

For you to save a layout, you can use the save function in the following manner:
```mcfunction
/function ghost_gui:save {slot:<SAVE NAME HERE>}
```
This will save the current window layout to the storage **ghost_gui main.saves.<NAME HERE>**, and as such, the name given to it must be a valid storage name.
![image](https://github.com/user-attachments/assets/cb7e2ce4-3f0c-456e-9165-d2271023b1ba)

And for loading the layout back from storage, you can use the load start function in the following manner:
```mcfunction
/function ghost_gui:load/start {slot:<SAVE NAME HERE>}
```
The layout stored to that name will then be spawned at the player's location and facing direction, with the windows displaced according to the previous anchor position. After the layout is loaded, the windows will then exit editable mode and the equipped functions will now be active and working according to their type.
![image](https://github.com/user-attachments/assets/a67ca552-de7d-4c0e-a6cb-d621e13d6eb2)

>[!WARNING]
>As of now, you cannot load a layout from storage for further editing, this shall come in a future update.
