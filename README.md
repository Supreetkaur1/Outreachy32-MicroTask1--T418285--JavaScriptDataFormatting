# Outreachy 32: Micro Task 1 (T418285) – JavaScript Data Formatting
T418285: Addressing the lusophone technological wishlist proposals - Create a JavaScript script to manipulate a json object and print it in a human legible format

## Task Overview

This repository contains my submission for **Outreachy Round 32 – Task T418284: Addressing the Lusophone Technological Wishlist Proposals**.

### Objective

The objective of this task is to:

* Manipulate a JSON object using JavaScript
* Convert raw data into a **human-readable format**
* Display the formatted output inside an HTML element

---

## Implementation Details

### Input

A predefined JavaScript array of objects:

```javascript
let data = [
  {
    "page_id": 6682420,
    "creation_date": "2021-09-13",
    "title": "André Baniwa"
  },
  ...
];
```

---

### Processing Logic

The implementation follows a structured approach:

### 1. Date Formatting

* Uses `Intl.DateTimeFormat` to convert dates from:

  ```
  YYYY-MM-DD → Month Day, Year
  ```
* Example:

  ```
  2021-09-13 → September 13, 2021
  ```

```javascript
const formatDate = new Intl.DateTimeFormat("en-US", {
    year: "numeric",
    month: "long",
    day: "numeric"
});
```

* A helper function `changeDateFormat()`:

  * Converts string → Date object
  * Validates the date
  * Returns formatted output

---

### 2. Data Transformation

Each object is converted into the required string format:

```
Article "ARTICLE TITLE" (Page ID PAGEID) was created at MONTH DAY, YEAR.
```

```javascript
function formatData(item) {
    return `Article "${item.title}" (Page ID ${item.page_id}) was created at ${changeDateFormat(item.creation_date)}.`;
}
```

---

### 3. Rendering to HTML

* Uses `.map()` to transform each object into an HTML `<p>` element
* Uses `.join("")` to combine all elements into a single string
* Injects the result into the DOM using `innerHTML`

```javascript
function renderData(data) {
    const output = data
        .map(item => `<p>${formatData(item)}</p>`)
        .join("");

    document.getElementById("results").innerHTML = output;
}
```

---

### Output Example

```
Article "André Baniwa" (Page ID 6682420) was created at September 13, 2021.
```

---

## Key Concepts Used

* JavaScript array methods: `map()`, `join()`
* DOM manipulation: `getElementById()`, `innerHTML`
* Date formatting using `Intl.DateTimeFormat`
* Template literals for string formatting
* Basic input validation

---

## Project Structure

```
.
├── Task 1 - Intern.html   # Main HTML file with embedded JavaScript
└── README.md              # Documentation
```

---

## How to Run

1. Download or clone this repository
2. Open the file in a browser:

   ```
   Task 1 - Intern.html
   ```
3. You will see:

   * **My code** → Displays the JavaScript implementation
   * **Results of my code** → Displays the formatted output

---

## Submission Details

* The HTML file has been committed to GitHub
* Submission sent via email:

  ```
  Subject: [Outreachy] Supreetkaur0602
  ```
* Contribution registered on the Outreachy platform

---

## Acknowledgment

Thank you for reviewing my submission. I look forward to your feedback and the opportunity to contribute further.
