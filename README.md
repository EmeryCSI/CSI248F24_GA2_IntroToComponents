# Renton Technical College CSI-248

<div align="center">  
    <img src="logo.jpg" alt="Logo">
    <h3 align="center">Guided Activity 2: React Native Basics</h3>
</div>

This repository is a part of CSI-248 at Renton Technical College.

## Guided Activity 2 - Setup

1. Clone the repository to your local machine. (Do not use OneDrive for assignments in this course!)
2. Make note of the folder where you cloned the repository.
3. After you have cloned this repository navigate to your local repository using the cd command.
4. Type `code .` to open the repository in Visual Studio Code.
5. Hit ctrl + ` to open the terminal.
6. Type `mkdir Screenshots` to add a screenshots folder to the project.

## Guided Activity Part 2: Intro to React Native - Components

1. We are going to build a basic UI to display a blog post using React Native components.
2. In the terminal, type `npx create-expo-app BlogApp --template blank` to create a new Expo project.
3. Once the project is created, navigate into it by typing `cd BlogApp`.
4. Open the project in Visual Studio Code by typing `code .`.
5. If you would like to be able to launch this application via web browser run `npx expo install react-dom react-native-web @expo/metro-runtime`
6. In the terminal, type `npx expo start` to launch the development server.
7. You can run the app on your physical device using the Expo Go app or in the browser by pressing `w`.

8. Open `App.js` and replace ALL of the code with the following:

```javascript
import React from 'react';
import { View, Text, StyleSheet } from 'react-native';

// This is the main component of our application
// It acts as a container for other components
export default function App() {
  return (
    // View is the fundamental UI building block in React Native
    // It's similar to a <div> in web development
    <View style={styles.container}>
      <Text style={styles.title}>Welcome to My Blog</Text>
    </View>
  );
}

// StyleSheet.create is used to define styles
// It's similar to CSS, but uses JavaScript objects
// This approach can provide better performance than inline styles
const styles = StyleSheet.create({
  container: {
    flex: 1, // This makes the container expand to fill the screen
    justifyContent: 'center',
    alignItems: 'center',
    backgroundColor: '#F5FCFF', // Light background color
  },
  title: {
    fontSize: 20,
    textAlign: 'center',
    margin: 10,
  },
});
```

8. Save `App.js` and notice the change in the app. Add a screenshot of this output to your Screenshots folder.

9. Inside the project folder, create a new folder named `components`.

10. In the `components` folder, create a new file named `BlogHeader.js`.

11. In `BlogHeader.js`, add the following code:

```javascript
import React from 'react';
import { View, Text, StyleSheet } from 'react-native';

// BlogHeader is a functional component that accepts props
// It demonstrates how to use props in a React Native component
const BlogHeader = ({ title, author }) => {
  return (
    <View style={styles.header}>
      {/* We use the title prop here */}
      <Text style={styles.headerText}>{title}</Text>
      {/* And the author prop here */}
      <Text style={styles.authorText}>By {author}</Text>
    </View>
  );
};

// Styles for the BlogHeader component
const styles = StyleSheet.create({
  header: {
    backgroundColor: '#4CAF50', // Green background
    padding: 20,
    width: '100%', // Full width of the parent
  },
  headerText: {
    color: 'white',
    fontSize: 18,
    fontWeight: 'bold',
  },
  authorText: {
    color: 'white',
    fontSize: 14,
  },
});

export default BlogHeader;
```

12. Go back to `App.js` and import the new component. Modify `App.js` to use the `BlogHeader` component:

```javascript
import React from 'react';
import { View, StyleSheet } from 'react-native';
import BlogHeader from './components/BlogHeader';

// This is the main component of our application
// It acts as a container for other components
export default function App() {
  return (
    // View is the fundamental UI building block in React Native
    // It's similar to a <div> in web development
    <View style={styles.container}>
      {/* BlogHeader component with props */}
      {/* We're passing 'title' and 'author' as props to BlogHeader */}
      {/* This demonstrates how data flows from parent to child components */}
      <BlogHeader title="My First Blog Post" author="John Doe" />
    </View>
  );
}

// StyleSheet.create is used to define styles
// It's similar to CSS, but uses JavaScript objects
// This approach can provide better performance than inline styles
const styles = StyleSheet.create({
  container: {
    flex: 1, // This makes the container expand to fill the screen
    backgroundColor: '#F5FCFF', // Light background color
  },
});
```

13. Now let's modify `BlogHeader.js` to accept props:

```javascript
import React from 'react';
import { View, Text, StyleSheet } from 'react-native';

const BlogHeader = ({ title, author }) => {
  return (
    <View style={styles.header}>
      <Text style={styles.headerText}>{title}</Text>
      <Text style={styles.authorText}>By {author}</Text>
    </View>
  );
};

const styles = StyleSheet.create({
  header: {
    backgroundColor: '#4CAF50',
    padding: 20,
    width: '100%',
  },
  headerText: {
    color: 'white',
    fontSize: 18,
    fontWeight: 'bold',
  },
  authorText: {
    color: 'white',
    fontSize: 14,
  },
});

export default BlogHeader;
```

14. Modify `App.js` to pass data to the `BlogHeader` component:

```javascript
import React from 'react';
import { View, StyleSheet } from 'react-native';
import BlogHeader from './components/BlogHeader';

export default function App() {
  return (
    <View style={styles.container}>
      <BlogHeader title="My First Blog Post" author="John Doe" />
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#F5FCFF',
  },
});
```

15. Data is now being moved from a parent component to a child component. Take a screenshot of the output and add to the Screenshots folder.

16. Now, let's create a component with state. Create a new file in the `components` folder named `LikeCounter.js`:

```javascript
import React, { useState } from 'react';
import { View, Text, TouchableOpacity, StyleSheet } from 'react-native';

// The LikeCounter component takes an 'initialLikes' prop
// This demonstrates how data can be passed from a parent component
const LikeCounter = ({ initialLikes }) => {
  // useState is a React Hook that lets you add state to functional components
  // It returns an array with two elements:
  // 1. The current state value (likes)
  // 2. A function to update that state (setLikes)
  // The argument passed to useState is the initial state value
  // Here, we're using the 'initialLikes' prop as the initial state
  const [likes, setLikes] = useState(initialLikes);

  // This function is called when the "Like" button is pressed
  // It uses the setLikes function to update the state
  const handleLike = () => {
    // When updating state based on the previous state,
    // it's best to use the functional form of setState
    // This ensures we're always working with the most up-to-date state
    setLikes(prevLikes => prevLikes + 1);
    
    // Alternatively, you could write:
    // setLikes(likes + 1);
    // But this might lead to issues if state updates happen very quickly
  };

  // The component's UI
  return (
    <View style={styles.container}>
      {/* Display the current number of likes */}
      <Text style={styles.likesText}>Likes: {likes}</Text>
      
      {/* TouchableOpacity is used to create a touchable button */}
      {/* When pressed, it calls the handleLike function */}
      <TouchableOpacity style={styles.button} onPress={handleLike}>
        <Text style={styles.buttonText}>Like</Text>
      </TouchableOpacity>
    </View>
  );
};

// Styles for the component
const styles = StyleSheet.create({
  container: {
    flexDirection: 'row',
    alignItems: 'center',
    padding: 10,
  },
  likesText: {
    fontSize: 16,
    marginRight: 10,
  },
  button: {
    backgroundColor: '#4CAF50',
    padding: 10,
    borderRadius: 5,
  },
  buttonText: {
    color: 'white',
    fontWeight: 'bold',
  },
});

export default LikeCounter;
```

Now, let's update the `App.js` file to show how props are passed to the `LikeCounter` component:

```javascript
import React from 'react';
import { View, StyleSheet } from 'react-native';
import BlogHeader from './components/BlogHeader';
import LikeCounter from './components/LikeCounter';

export default function App() {
  return (
    <View style={styles.container}>
      {/* The BlogHeader component receives 'title' and 'author' as props */}
      <BlogHeader title="My First Blog Post" author="John Doe" />
      
      {/* The LikeCounter component receives 'initialLikes' as a prop */}
      {/* This demonstrates how we can pass data from a parent component to a child component */}
      <LikeCounter initialLikes={0} />
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#F5FCFF',
  },
});
```

17. Take a screenshot of the rendered app and save it in the Screenshots directory.

18. Let's create a color picker component to demonstrate more complex state management. Create a new file in the `components` folder named `ColorPicker.js` and add the following code:


import React, { useState } from 'react';
import { View, Text, TouchableOpacity, StyleSheet } from 'react-native';

const ColorPicker = ({ initialColor }) => {
  // We use useState to manage the current color
  // initialColor is used as the initial state value
  const [currentColor, setCurrentColor] = useState(initialColor);

  // Array of color options
  // These are hex color codes representing different colors
  const colors = ['#FF0000', '#00FF00', '#0000FF', '#FFFF00', '#FF00FF', '#00FFFF'];

  // Function to handle color selection
  // This function is called when a color is tapped
  const handleColorChange = (color) => {
    setCurrentColor(color); // Update the currentColor state
  };

  return (
    <View style={styles.container}>
      <Text style={styles.title}>Color Picker</Text>
      {/* This View displays the currently selected color */}
      {/* The style prop here combines predefined styles with dynamic backgroundColor */}
      {/* [styles.colorPreview, { backgroundColor: currentColor }] is an array of style objects */}
      {/* styles.colorPreview contains base styles defined in StyleSheet.create() */}
      {/* { backgroundColor: currentColor } is an inline style object that overrides or adds to the base styles */}
      {/* This allows the preview's background color to update dynamically as currentColor changes */}
      <View style={[styles.colorPreview, { backgroundColor: currentColor }]} />
      <View style={styles.colorOptions}>
        {/* Map over the colors array to create TouchableOpacity components for each color */}
        {colors.map((color) => (
          <TouchableOpacity
            key={color} // Use the color itself as a unique key
            style={[styles.colorOption, { backgroundColor: color }]}
            onPress={() => handleColorChange(color)} // Call handleColorChange when pressed
          />
        ))}
      </View>
    </View>
  );
};

// Styles for the ColorPicker component
const styles = StyleSheet.create({
  container: {
    padding: 10,
    alignItems: 'center',
  },
  title: {
    fontSize: 18,
    fontWeight: 'bold',
    marginBottom: 10,
  },
  colorPreview: {
    width: 100,
    height: 100,
    borderRadius: 50, // Makes it circular
    marginBottom: 20,
  },
  colorOptions: {
    flexDirection: 'row',
    justifyContent: 'center',
    flexWrap: 'wrap', // Allows colors to wrap to next line if there are many
  },
  colorOption: {
    width: 40,
    height: 40,
    borderRadius: 20, // Makes each color option circular
    margin: 5,
  },
});

export default ColorPicker;

Key points to understand:

1. **useState Hook**: 
   - `const [currentColor, setCurrentColor] = useState(initialColor);`
   - This line sets up a state variable `currentColor` and a function to update it `setCurrentColor`.
   - The initial value of `currentColor` is set to `initialColor`, which is passed as a prop.

2. **Color Options**:
   - `const colors = ['#FF0000', '#00FF00', '#0000FF', '#FFFF00', '#FF00FF', '#00FFFF'];`
   - This array defines the color options available in the picker.
   - Each color is represented by its hexadecimal code.

3. **handleColorChange Function**:
   - This function is called when a color is selected.
   - It updates the `currentColor` state with the newly selected color.

4. **Rendering**:
   - The component renders a title, a preview of the current color, and a set of color options.
   - The color preview is a `View` component with its background color set to the current selected color.
   - The color options are rendered using the `map` function, which creates a `TouchableOpacity` component for each color in the `colors` array.

5. **TouchableOpacity**:
   - Each color option is wrapped in a `TouchableOpacity`, which makes it respond to touch events.
   - When pressed, it calls `handleColorChange` with the corresponding color.

6. **Styling**:
   - The `StyleSheet.create` method is used to define styles for the component.
   - The `colorPreview` and `colorOption` styles use `borderRadius` to create circular shapes.
   - The `colorOptions` container uses `flexWrap: 'wrap'` to allow the color options to flow onto multiple lines if there are many colors.

This component demonstrates several important React Native concepts: state management with hooks, dynamic rendering with `map`, handling user interactions with `TouchableOpacity`, and applying dynamic styles based on state and props.

## Guided Activity Part  Submission

1. Ensure all your changes, including the new ColorPicker component, are saved.
2. Type `git add .` to stage all updated files.
3. Type `git commit -m "Guided Activity 2 Complete"`.
4. Type `git push`

If you have any questions about this assignment, including the new ColorPicker component, please reach out to myself or our TA for this course.
Feel free to message your instructor or the
