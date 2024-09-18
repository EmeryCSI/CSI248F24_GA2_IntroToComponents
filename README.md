Certainly! I'll provide step-by-step instructions on how to create a demo project for learning about basic component creation in React Native, including components with props and state. Here's an updated version of the assignment focused on React Native:

# Renton Technical College CSI-248
<br />
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
2. In the terminal, type `npx create-expo-app BlogApp` to create a new Expo project.
3. Once the project is created, navigate into it by typing `cd BlogApp`.
4. Open the project in Visual Studio Code by typing `code .`.
5. In the terminal, type `npx expo start` to launch the development server.
6. You can run the app on your physical device using the Expo Go app, or set up an emulator/simulator.

7. Open `App.js` and replace ALL of the code with the following:

```javascript
import React from 'react';
import { View, Text, StyleSheet } from 'react-native';

export default function App() {
  return (
    <View style={styles.container}>
      <Text style={styles.title}>Welcome to My Blog</Text>
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    justifyContent: 'center',
    alignItems: 'center',
    backgroundColor: '#F5FCFF',
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

const BlogHeader = () => {
  return (
    <View style={styles.header}>
      <Text style={styles.headerText}>My Blog Header</Text>
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
});

export default BlogHeader;
```

12. Go back to `App.js` and import the new component. Modify `App.js` to use the `BlogHeader` component:

```javascript
import React from 'react';
import { View, StyleSheet } from 'react-native';
import BlogHeader from './components/BlogHeader';

export default function App() {
  return (
    <View style={styles.container}>
      <BlogHeader />
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


Key points to understand:

1. Props: Props (short for "properties") are a way to pass data from parent components to child components. In this example, `App.js` passes the `initialLikes` prop to the `LikeCounter` component.

2. useState: This is a React Hook that allows functional components to have state. It takes an initial state value as an argument and returns an array with two elements: the current state value and a function to update it. When the state updating function is called, React re-renders the component with the new state.

3. State updates: When updating state based on its previous value, it's best to use the functional form of the state updating function (e.g., `setLikes(prevLikes => prevLikes + 1)`). This ensures that you're always working with the most up-to-date state value, which is important in cases where multiple state updates might happen in quick succession.

These concepts form the foundation of building interactive components in React Native. By understanding props and state, you can create components that can receive data from their parents and manage their own internal state, allowing for dynamic and interactive user interfaces.

18. Take a final screenshot of the rendered app and save it in the Screenshots directory.

## Explanation of Components

1. `App.js`: This is the main component of our application. It serves as a container for other components and manages the overall structure of the app.

2. `BlogHeader.js`: This component demonstrates the use of props. It receives `title` and `author` as props from its parent (`App.js`) and displays them. This shows how data can be passed down from parent to child components.

3. `LikeCounter.js`: This component demonstrates the use of both props and state. It receives an `initialLikes` prop and uses the `useState` hook to manage its own state. The `handleLike` function updates the state when the button is pressed, causing the component to re-render with the new like count.

React Native uses a similar component-based architecture to React, but with native mobile components instead of web components. The `View` component is similar to a `div` in web development, while `Text` is used for displaying text. `TouchableOpacity` is a commonly used component for creating touchable elements like buttons.

The `StyleSheet.create` method is used to define styles for our components. This is similar to CSS in web development but uses JavaScript objects to define styles.

By building this simple blog post app, you've learned about creating basic components, passing props, and managing state in a React Native application.

## Guided Activity Part 3 Submission

1. Type `git add .` to stage all updated files.
2. Type `git commit -m "Guided Activity 2 Complete"`.
3. Type `git push`.

If you have any questions about this assignment please reach out to myself or our TA for this course.
Feel free to message your instructor or the TA on Canvas if you have any questions.
