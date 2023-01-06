# XWiki-Checkboxed-Task-Macro
This [XWiki](https://github.com/xwiki/xwiki-platform) macro adds a **task with checkbox** macro and an event listener for ticking completed tasks off using the checkboxes. Additionally there is a a configurable **task report** macro that lists tasks from a given space.

## Installation
Head over to [Releases](https://github.com/jmiba/XWiki-Checkboxed-Task-Macro/releases), download the .xar file, and import it in the [Wiki administration section](https://extensions.xwiki.org/xwiki/bin/view/Extension/Administration%20Application) under "Content" -> "Import"

## Configure CKEditor

In order to make best use of the macro, add the following CKeditor configuration to your editor through the [dedicated "WYSIWYG Editor" section](https://extensions.xwiki.org/xwiki/bin/view/Extension/CKEditor%20Integration/#HAdministrationSection) in the [Wiki administration](https://extensions.xwiki.org/xwiki/bin/view/Extension/Administration%20Application):


```
config['xwiki-macro'] = config['xwiki-macro'] || {};
config['xwiki-macro'].insertButtons = [
  {
    insertDirectly: false,
    macroCall: {
      name:'checktask',
      inline:'enforce',
    }
  }
];
```

## Macros and components 

* **CheckboxedTask**: Contains the **checktask** macro that inserts checkboxed tasks in pages amd a JavaScirpt listener that listens for checking/unchecking events
* **CheckboxedTaskListener**: Event listener that listens for creating and updating tasks on pages, adding xobjects to the respective pages
* **CheckboxUpdater**: Is called by the JavaScript listener to update the xobject of a task when checked or unchecked
* **Task Class**:  Xobject class that defines the properties of tasks to be saved 
* **CheckboxedTaskReport**: Contains the macro **reportchecktasks** that inserts a task report in pages using the default **live data** macro. Also contains another JavaScript listener listening for cheking/unchecking events within the live data table.
* **TasksJSON**: Defines the database query and formats the input for the live data macro in  the task report
* **CheckboxedTaskTranslations**: Contains the localized labes of the task and task report macros
