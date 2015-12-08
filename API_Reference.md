# Core #
Containers:
  * Middix.Lib - Libs are placed here, e.g. Middix.Lib.File
  * Middix.Kernel - System Calls
  * Middix.User - User Information
  * Middix.Temp - Temporary Variable Storage.
  * Middix.Registry- Middix Registry
  * Middix.Clipboard - Object.
  * Middix.TempCount - Amount of temporary items.
  * Middix.Divs - Div ID Assignment Internal.

Functions:
  * Middix.GetID() - Used for making games / other core programs.
  * Middix.Escape(text) - Used for double escaping in apps.
  * Middix.Processes - Process functions
    * New(Process Path, Process Parameters/Arguments) - e.g. "Apps/foo.mxs",null
    * NewApp(App Name, Parameters) - e.g. "filebrowse",null
    * AppFile(Filename) - Opens a file with the default app, e.g. .txt in textedit.
    * Kill(Process ID) - Kills (forcefully ends) a process.
    * End(Process ID) - Ends a process.
  * Middix.Registry.UserData[ENTRY](ENTRY.md) - Registry Access
  * Middix.Registry.Data[ENTRY](ENTRY.md) - System Registry (Read Only)
  * Middix.Kernel.Logout() - No prize for guessing what this does.
  * Middix.GetFile(Filename) - Used for retrieving files like images through security.

Admin Functions:
  * Middix.NewUser(Username,Fullname,Password,Admin,Theme,Wallpaper) - Creates new user.
  * Middix.RemoveUser(Username) - Erases a user and home directory.
  * Middix.Assosciate(Filetype,SmallIcon,BigIcon,App,fName,Description) - Assosciates a filetype with an installed App.
  * Middix.Unassosciate(Filetype)

# Libraries #
Ajax Request:
  * Object = Middix.Lib.Ajax(Pause JS Execution? : Boolean)
  * Object.Request(URL : String)
  * Object.onRecieved = function()
  * Object.responseText : String

Dialogs:
  * Middix.Dialogs.Alert(Process ID : Int, Title : String, Text : String) - Displays an alert box with title Title, content Text.

Files:
  * Middix.Lib.File.RmDir(Path : String) - Removes directory Path.
  * Middix.Lib.File.MkDir(Path : String) - Creates directory Path.
  * Middix.Lib.File.Copy(Path : String, NewPath : String) - Copies Path to NewPath.
  * Middix.Lib.File.Rename(Path : String, NewName : String) - Renames file Path to NewName.
  * Middix.Lib.File.Delete(Path : String) - Have a guess.
  * Middix.Lib.File.Read(Path : String) - Returns the contents of the file as a String.
  * Middix.Lib.File.Write(Path : String, Contents : String) - Writes new file contents.
  * Middix.Lib.File.Exist(Path : String) - Returns string "true" if file exists.
  * Middix.Lib.File.ReadDirectory(Path : String) - Returns a multidimensional array of the directory contents. e.g. ReturnedArray[- File Names: Strings, 1 - Dir Names: Strings](0.md)[index](index.md)

Filenames:
  * Middix.Lib.Filenames.Trim(Filename : String, Length : Int, Lines : Int) - Shortens a filename to Length characters over Lines lines.
  * Middix.Lib.Filenames.Filter(Filename : String) - Returns the filename stripped of forbidden Middix characters.
  * Middix.Lib.Filenames.GetType(Filename : String) - Returns the file extension (String) of Filename, or "unknown".
  * Middix.Lib.Filenames.GetName(Filename : String) - Will get the actual name of the file from a path, e.g. "./Public/something/foo.txt" would return "foo.txt"
  * Middix.Lib.Filenames.GetApp(Filename : String) - Returns the default App (String) that the filetype is assigned too. e.g. "file/foo.txt" returns "textedit"
  * Middix.Lib.Filenames.GetFileLong(Filename : String) - Gets the long description of the file type, e.g. "./foo.txt" would return "Text File".
  * Middix.Lib.Filenames.GetParent(Filename : String) - Returns the path to the filename's parent folder.

MD5:
  * Middix.MD5(Text : String) - MD5 hashes the Text.

Reflection:
  * Middix.Lib.Reflection(Image Path : String) - Retuns the path (String) of a reflected version of the image.

Zip:
  * Middix.Lib.Zip.Extract(Zip Path : String, Target Path : String) - Extracts Zip Path to Target Path.

# WM #
Create Window Object
  * Window = Middix.WM.NewWindow(PID,Type,Taskbar,Icon,BigIcon) - Creates a new window.
    * PID - Process ID, can be retrieved in your app via this.ID
    * Type - Window type, 0 - borderless, 1 - normal, 2 - dialog, 3 - resizable.
    * Taskbar - Boolean, show in taskbar.
    * Icon, Big Icon - 22x22 and 32x32 icons for the window, can be set to null for default icon.

Window Object Functions
  * Window.Move([X,Y]) - Moves window to XY position on screen.
  * Window.Resize([Width,Height])
  * Window.Minimize()
  * Window.Maximize()
  * Window.Title(Title : String) - Changes the window title.
  * Window.Content(Content : String) - Changes the content of the window.
  * Window.Focus() - Focuses the window.
  * Window.Center() - Moves the window to center of the screen.
  * Window.Close() - Closes the window. When last window is closed, process is ended.

# Widgets #
Middix.Widget

  * Widget = Middix.Widget. WIDGET (Process ID)

  * All Widgets Have Properties:
    * .Size - [Width,Height] Change widget size BEFORE it's been rendered.
    * .Generate() - Return the code.
    * .Resize([Width,Height]) - Resize widget AFTER it's been rendered.

Additional Properties

  * .Button - Standard button.
    * .Text - Button label / caption

  * .ImageButton - An image with button functions.
    * .Text - Mouseover text.
    * .Icon - Icon to appear.

  * .BigList - A large horizontal list, used in the old Middix UI.
    * .Add(Caption, Icon) - Add an entry to the list before rendering.

  * .SmallList - The small lists seen at the top of apps.
    * .Add(Caption, Icon) - Add an entry to the list before rendering.

  * .IconPanel - Code generated should be put in a frame. Used to generate icon panels.
    * .Add(Caption, Icon) - Adds an icon, and returns the Icon ID.
    * .Reset() - Removes all icons in the list.
    * .Select(Icon ID) - Highlights the Icon ID.
    * .UnSelect(Icon ID) - Un ""

  * .SideBox - Similiar to those in Windows XP
    * .Text - Changes text on the sidebox heading.
    * .Content(Content) - Sets contents of sidebox.

  * .Frame - Frames should always be included in windows.
    * .Content(Content) - Sets contents of frame.

  * .Text - Large text edit box.
    * .SetText(Text)
    * .GetText() - Returns text in box.

  * .iFrame - Iframe.
    * .Navigate(URL) - Changes iframe location.
    * .Back() - Sends the iframe back a page.
    * .Forward() -         ""    forward

  * .Input - Small input box.
    * .SetText(Text)
    * .GetText() - Returns text in box.

  * .PasswordInput - Small input box.
    * .SetText(Text)
    * .GetText() - Returns text in box.

  * .Dropdown - Dropdown list.
    * .Add(Caption) - Adds to combo list, and returns Index.
    * .SetValue(Index) - Changes value of box to Index.
    * .GetValue() - Returns value of box.