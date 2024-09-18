# Renton Technical College CSI-248

<br />

<div align="center">  
    <img src="logo.jpg" alt="Logo">
    <h3 align="center">Guided Activity 2</h3>
</div>

This repository is a part of CSI-248 at Renton Technical College.

## Guided Activity 2 - Setup

1. Clone the repository to your local machine. (Do not use OneDrive for assignments in this course!)
2. Make note of the folder where you cloned the repository.
3. After you have cloned this repository navigate to your local repository using the cd command.
4. Type `code .` to open the repository in Visual Studio Code.
5. Hit ctrl + ` to open the terminal.
6. Type `mkdir Screenshots` to add a screenshots folder to the project.
   ![Alt text](<Images/GA2 - Setup - Step 6.png>)

## Guided Activity Part 2 Intro To React - Components

1. We are going to build a basic UI to display a blog post out out components.
2. In the terminal type `npm create vite .` to create a vite project in the current directory.
3. Name the project guidedactivity2.
4. Choose React as the Framework.
5. Choose JavaScript as the variant.
   ![Alt text](<Images/GA2 - Components - Step 5.png>)

6. When the project has generated type `cd guidedactivity2`.
7. Type `npm install`.
8. Type `npm run dev` to launch the demo project.
   ![Alt text](<Images/GA2 - Components - Step 8.png>)

9. Click the local host link to launch the project.
   ![Alt text](<Images/GA2 - Components - Step 9.png>)

10. Take a screenshot of the template project running and save in screenshots.
    ![Alt text](<Images/GA2 - Components - Step 10 cropped.png>)

11. In the src folder replace ALL of the code in App.jsx with the following:
    ![Alt text](<Images/GA2 - Components - Step 11.png>)

12. Save App.jsx and notice the change in the browser. Add a screenshot of this output.
    ![Alt text](<Images/GA2 - Components - Step 12 cropped.png>)

13. Inside of src create a folder named components.
14. Create a component named BlogHeader.jsx
    ![Alt text](<Images/GA2 - Components - Step 14.png>)

15. In BlogHeader.jsx add the following code:

    ![Alt text](<Images/GA2 - Components - Step 15.png>)

16. Go back to App.jsx and import the new component and render the component after the h1:
    ![Alt text](<Images/GA2 - Components - Step 16.png>)

17. Now that we see our component is working lets try to pass some data to it with props
18. Modify BlogHeader.jsx to take a props parameter and display information from the props in the component:
    ![Alt text](<Images/GA2 - Components - Step 18.png>)

19. Modify App.jsx to pass data to the BlogHeader component:
    ![Alt text](<Images/GA2 - Components - Step 19.png>)

20. Data is now being moved from a parent component to a child component. Take a Screenshot of the output and add to screenshots.
    ![Alt text](<Images/GA2 - Components - Step 20 cropped.png>)

21. Repeat this process for a BlogBody component and a BlogFooter component.
22. Code for BlogBody:

    ![Alt text](<Images/GA2 - Components - Step 22.png>)

23. Code for BlogFooter:

    ![Alt text](<Images/GA2 - Components - Step 23.png>)

24. Import BlogBody and BlogFooter into App.jsx and render them while passing some data to the props
25. Updated code for App.jsx. Notice how components can also use self-closing tags.

    ![Alt text](<Images/GA2 - Components - Step 25.png>)

26. Take a screenshot of the rendered webpage and save in screenshots directory.
    ![Alt text](<Images/GA2 - Components - Step 26 cropped.png>)

## Guided Activity Part 3 Submission (You can also use GitHub desktop to submit)

1. Type `git add .` to stage all updated files.
2. Type `git commit -m "Guided Activity 2 Complete"`.
3. Type `git push`.

If you have any questions about this assignment please reach out to myself or our TA for this course.

Feel free to message your instructor or the TA on Canvas if you have any questions.
