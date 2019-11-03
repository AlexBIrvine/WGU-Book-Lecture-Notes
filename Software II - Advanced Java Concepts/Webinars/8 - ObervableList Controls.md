---
Date: 2019/10/09
Length: 51:02
Note Taker: Alex Irvine
Speaker: Malcolm Wabara
---

Video: [ObservableList Controls](https://wgu.adobeconnect.com/pycbm8bttaol/)

<u>**Summary**</u>:

Plan:

- Understand the ObservableList Interface
- Populate ObservableList Controls with Data
- Detect Selected items from ObservableList Controls

---

## The OberservableList (00:25 - 02:00)

Works with JavaFX controls such as TableViews, ListViews and ComboBoxes
Similar to ArrayList.

How it's created:  
`ObservableList<String> variable = FXCollections.observableArrayList()`

Once it's created, you can add it to a control that supports it.

---

## The ListView Control (02:00 - 06:36)

list of items you can select.  
![8.1](./img/8.1.jpg)

How it's created:  
`ListView<String> variable = new List<>();`

To populate the ListView, pass an ObservableList to the ListView constructor:

```java
ObservableList<String> olVariable = FXCollections.observableArrayList("Alex", "John", "Joe");
ListView<String> lvVariable = new ListView<>(olVariable);
```

To link ObservableList & ListView after ListView creattion, use `getItems().addAll()` or `getItems().setAll()`.  
[What is the difference? There has to be one...]

```java
lvVariable.getItems().addAll(olVariable);
//OR
lvVariable.getItems().setAll(olVariable);
```

With JavaFXML being used, the `lvVariable` will be the FXML variable.

---

## Programming Exercise (06:37 - 18:43) - Create & populate list view

In SceneBuilder, the teacher does the following:

1. Adds a `ListView` to an empty `AnchorPane`.
2. Assigns the fxid of "myListView" to the `ListView`.

(Inside the FXMLDocumentController)

```java
@FXML private ListView<String> myListView;

//Create ObservableList
ObservableList<String> shoppingList = FXCollections.observableArrayList("Apples", "Milk", "Cheese");


//Created in every new JavaFX project by NetBeans
@Override
public void initialize(URL url, ResourceBundle rb) {

  //Populate ListView
  myListView.setItems(shoppingList);
}
```

---

## Programming Exercise (18:50 - 29:03) - Adding items to a ListView from a file

The teacher goes to the directory that holds the source code & creates a text file `groceries.txt`.  
In this file, each line is a new item on the list.  
Later he renames the file to `Items.txt`. The list contains random items.

(Back in the FXMLDocumentController)

```java
@Override
public void initialize(URL url, ResourceBundle rb) {

  //using try-catch initialize cannot handle throw
  //Open and load file content
  try {

    //load file
    File file = new File("Items.txt");
    Scanner inputFile = new Scanner(file);

    //load data from file into shoppingList
    while( inputFile.hasNext() ) {
      shoppingList.add( inputFile.nextLine() );
    }

    //Populate ListView
    myListView.setItems(shoppingList);
  }
  catch(IOException e) {
    System.out.println("Error");
  }
}
```

---

## Detecting a Selected item in a ListView Control (29:07 - 36:00)

ObservableList provides `getSelectionModel()` to specify `single` or `multiple` selections.  
(Default option is `single`)

After `getSelectionModel()` is called, `getSelectedItem()` can be used. This returns the selected item.

(Back in the FXMLDocumentController)

```java
@Override
public void initialize(URL url, ResourceBundle rb) {

  //using try-catch initialize cannot handle throw
  //Open and load file content
  try {

    //load file
    File file = new File("Items.txt");
    Scanner inputFile = new Scanner(file);

    //load data from file into shoppingList
    while( inputFile.hasNext() ) {
      shoppingList.add( inputFile.nextLine() );
    }

    //Populate ListView
    myListView.setItems(shoppingList);
  }
  catch(IOException e) {
    System.out.println("Error");
  }

  //Create an event listener, displays selected item
  myListView.getSelectionModel().selectedItemProperty().addListener(
    event -> {
      String selectedItem = myListView.getSelectionModel().getSelectedItem();
      System.out.println(selectedItem);
    }
  );
}
```

---

## The ComboBox Control (36:04 - 36:54)

Allows you to select an item from a **Drop down** list.  
![8.2](./img/8.2.jpg)

How it's created:  
`ListView<String> variable = new List<>();`

Has `getValue()` and `setValue()` methods.

---

## Programming Exercise (36:55 - END) - Setting up a ComboBox

In SceneBuilder, the teacher:

1. Adds a `ComboBox` control to the existing `AnchorPane`.
2. Assigns the fxid of "myComboBox" to the `ComboBox`.
3. Changes the `On Action` field's value to "handleCBActions".

(Back in the FXMLDocumentController)

```java
//Add the following to the variables near the top
@FXML private ComboBox<String> myComboBox;

//Handles event for combobox (aka, item selection)
//Prints out selected item's index
@FXML
void handleCBActions (ActionEvent event) {
  System.out.println( myComboBox.getSelectionModel().getSelectedIndex() );
}



@Override
public void initialize(URL url, ResourceBundle rb) {

  //using try-catch initialize cannot handle throw
  //Open and load file content
  try {

    //load file
    File file = new File("Items.txt");
    Scanner inputFile = new Scanner(file);

    //load data from file into shoppingList
    while( inputFile.hasNext() ) {
      shoppingList.add( inputFile.nextLine() );
    }

    //Populate ListView
    myListView.setItems(shoppingList);

    //Populate ComboBox & Set Default item to the first item
    myComboBox.setItems(shoppingList);
    myComboBox.getSelectionModel().select(0);       //0 = index of ObservableList, aka 1st item
  }
  catch(IOException e) {
    System.out.println("Error");
  }

  //Create an event listener, displays selected item
  myListView.getSelectionModel().selectedItemProperty().addListener(
    event -> {
      String selectedItem = myListView.getSelectionModel().getSelectedItem();
      System.out.println(selectedItem);
    }
  );
}
```
