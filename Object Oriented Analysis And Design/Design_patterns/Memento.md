### Where to Use

Use the Memento Pattern in the following scenarios:

- When you need to save and restore the state of an object.
- When you want to implement undo/redo functionality.
- When you need to preserve the encapsulation boundaries of an object without exposing its internals.

### Code Explanation

#### Memento Pattern Implementation

##### Step 1: Define the Memento

```java
public class Memento {
    private final String state;

    public Memento(String state) {
        this.state = state;
    }

    public String getState() {
        return state;
    }
}

```

- The `Memento` class stores the state of the `Originator`. It provides a method to retrieve the stored state.

##### Step 2: Define the Originator

```java
public class Originator {
    private String state;

    public void setState(String state) {
        this.state = state;
        System.out.println("State set to: " + state);
    }

    public String getState() {
        return state;
    }

    public Memento saveStateToMemento() {
        return new Memento(state);
    }

    public void getStateFromMemento(Memento memento) {
        state = memento.getState();
    }
}

```

- The `Originator` class can create a memento of its current state and restore its state from a memento.

##### Step 3: Define the Caretaker

```java
import java.util.ArrayList;
import java.util.List;

public class Caretaker {
    private List<Memento> mementoList = new ArrayList<>();

    public void add(Memento state) {
        mementoList.add(state);
    }

    public Memento get(int index) {
        return mementoList.get(index);
    }
}

```

- The `Caretaker` class is responsible for keeping the mementos. It can store multiple mementos and retrieve them when needed.

##### Step 4: Client Code

```java
public class MementoPatternExample {
    public static void main(String[] args) {
        Originator originator = new Originator();
        Caretaker caretaker = new Caretaker();

        originator.setState("State #1");
        originator.setState("State #2");
        caretaker.add(originator.saveStateToMemento());

        originator.setState("State #3");
        caretaker.add(originator.saveStateToMemento());

        originator.setState("State #4");

        System.out.println("Current State: " + originator.getState());
        originator.getStateFromMemento(caretaker.get(0));
        System.out.println("First saved State: " + originator.getState());
        originator.getStateFromMemento(caretaker.get(1));
        System.out.println("Second saved State: " + originator.getState());
    }
}

```

### Real World Example

Consider a text editor where you need to implement undo functionality. The Memento Pattern can help save and restore the state of the text being edited.

```java
// Memento class
public class TextMemento {
    private final String text;

    public TextMemento(String text) {
        this.text = text;
    }

    public String getText() {
        return text;
    }
}

// Originator class
public class TextEditor {
    private String text;

    public void setText(String text) {
        this.text = text;
        System.out.println("Text set to: " + text);
    }

    public String getText() {
        return text;
    }

    public TextMemento saveToMemento() {
        return new TextMemento(text);
    }

    public void restoreFromMemento(TextMemento memento) {
        text = memento.getText();
    }
}

// Caretaker class
import java.util.Stack;

public class TextEditorCaretaker {
    private Stack<TextMemento> mementoStack = new Stack<>();

    public void save(TextEditor editor) {
        mementoStack.push(editor.saveToMemento());
    }

    public void undo(TextEditor editor) {
        if (!mementoStack.isEmpty()) {
            editor.restoreFromMemento(mementoStack.pop());
        } else {
            System.out.println("No states to undo.");
        }
    }
}

// Client code
public class TextEditorApplication {
    public static void main(String[] args) {
        TextEditor editor = new TextEditor();
        TextEditorCaretaker caretaker = new TextEditorCaretaker();

        editor.setText("Version 1");
        caretaker.save(editor);

        editor.setText("Version 2");
        caretaker.save(editor);

        editor.setText("Version 3");

        System.out.println("Current Text: " + editor.getText());
        caretaker.undo(editor);
        System.out.println("After undo: " + editor.getText());
        caretaker.undo(editor);
        System.out.println("After undo: " + editor.getText());
    }
}

```

In this example, the `TextEditor` class is the originator, the `TextMemento` class stores the text state, and the `TextEditorCaretaker` class manages the memento stack to handle undo operations. This setup allows the editor to revert to previous states seamlessly, implementing a basic undo functionality.