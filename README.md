# Week 8 Practical 1: localStorage and sessionStorage

In this practical you will design and implement client-side data storage to improve the user experience for a handful of webpages. 

## Stage 1: Viewing / modifying localStorage via Chrome for debugging purposes

It's often helpful to be able to see / edit localStorage key-value pairs in the browser so you can tell if your code is working and fix any problems created by broken code.

Run stage1/index.html in Chrome. You will see three paragraphs that say:

```
item1 is null
item2 is null
item3 is null
```

Look at the code in main.js. The first three lines of code are retrieving stored values with the keys `item1`, `item2`, and `item3`. Because we haven't stored anything with these keys yet, the values will be null. 

The rest of the code creates a paragraph for each item and displays it in the `div` with id `output`.

Next, add some data to localStorage using Chrome (not code):

1. Open Chrome Developer tools and go to the Application tab.
2. Find localStorage under the heading "Storage". If this item is collapsed, click the heading to open it. Click on the URL matching the URL of your page to see the data it has stored in localStorage.
    - You will see an empty table with column headings "Key" and "Value".

![Empty localStorage](images/emptyStorage.png)

4. Double click in table just under the "Key" heading. When the row becomes editable, type `item1`. Double click in the "Value" column next to `item1` and type a message.
5. Refresh the page and you should see the first paragraph update to show the value you have added.
![localStorage contains one key value pair](images/firstValue.png)
    - If you close and reload the tab, you will see that the key-value pair is still in localStorage. localStorage is browser-specific. So, if you run the HTML page in a different browser, it will not have any data.
6. Add `item2` and `item3` to localStorage. Try storing values of different data types.
7. You can edit existing values in localStorage - double click on the value and change it.
8. Try deleting data: right-click on the key name to delete the pair.

You can view and modify data stored in sessionStorage in the same way. Just go to the Session Storage area in the Application tab of Chrome Developer tools.

## Stage 2: Getting and setting localStorage data
You will need your completed code for last practical, exercise 2.1 (the theme selector). You can also use the sample solution for that exercise. The website that you created for exercise 2.1 in the last practical allowed the user to change the theme of the website. Enhance that website by saving the user’s preference in `localStorage`. If the user has a saved preference, the website should automatically render using their preferred theme. Here are the steps:

1.	Decide the structure of the stored preference data. There are multiple possible structures that would be appropriate.

2.	When your script loads, it should check if the user has a preference. Remember from lecture that you can check if a key exists in `localStorage` using `localStorage.getItem(keyName)`. If the key does not exist, `getItem` will return `null`.

3.	If and only if the user has a saved preference, apply the preferred theme AND set the corresponding radio button’s checked property. 

4.	When the user chooses a different theme, update the stored theme using `localStorage.setItem(keyName, value)`

If you are storing data in a form more complex than a basic string (e.g. an object literal or class), don't forget to:
- use `JSON.stringify(yourData)` to correctly format the data for storage, - and use `JSON.parse(localStorage.getItem("yourKey"))` to convert the stored data to an object literal. 

Note: if you create a class to represent a theme, you will need to use the parsed object literal to create a new instance of your class. Ask for help if you're not sure how to do this!

Test that everything is working by choosing a new theme then closing your browser and reopening the page. If everything has worked, the selected theme should be remembered.

## Stage 3: Passing data between HTML pages with sessionStorage
Sometimes, you might want to pass data from one HTML page to another but you don't need to store it in the browser long term. `sessionStorage` is useful for this.
1. Create a folder for this exercise then add two HTML files called index.html and preview.html.
2. Create a Javascript file called storeText.js and link it to index.html.
3. Create another Javascript file called readText.js and link it to preview.html.
4. Add links in the HTML pages so that you can navigate between them.
5. In index.html, add a `textarea` element. In the associated Javascript file write some code to store the contents of the textarea in `sessionStorage` every time there is an input event. It should look something like this:
```
document.getElementById("your-textarea-id").addEventListener("input", function (event) {
    // Your code to store the text area contents
})
```
6. In preview.html, add a paragraph element. In the associated Javascript file write some code to get the saved text out of `sessionStorage` and display it in the paragraph. Don't forget to check that the saved text is not `null` before displaying it.
7. Test your code by running index.html, typing something in the textarea, then navigating to see preview.html to see if is displayed. 
8. If you navigate back to index.html, you may see that the textarea is empty. Modify your code so that the textarea will display any previously saved text. Try not to repeat any code you've already written! 
