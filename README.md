# Fed
1.npx start
2. Set-ExecutionPolicy -ExecutionPolicy Bypass -Scope Process
3. npx create-react-app my-student-app
4. cd my-student-app
5. You should see something like: PS C:\Users\admin\Desktop\Student\my-student-app>
6. npm start

7. Compiled successfully!

Local: http://localhost:3000

import React, { useState, useEffect } from "react";

import "./App.css";

function App() {

const [students, setStudents] = useState([]);

const [loading, setLoading] = useState(true);

const [error, setError] = useState("");

useEffect(() => {

fetch("/student.json")

.then(response => {

if (!response.ok) {

throw new Error("Failed to load student data");

}

return response.json();

})

.then(data => {

setStudents(data);

setLoading(false);

}) Frontend Design Lab

MURALI M, NCJ

.catch(() => {

setError("Error: Unable to load student data.");

setLoading(false);

});

}, []);

return (

<div className="container">

<h2>Student Details</h2>

{loading && <p>Loading...</p>}

{error && <p className="error">{error}</p>}

{!loading && !error && (

<table>

<thead>

<tr>

<th>Register No</th>

<th>Name</th>

<th>Course</th>

<th>Marks</th>

</tr>

</thead> Frontend Design Lab

MURALI M, NCJ

<tbody>

{students.map(student => (

<tr key={student.registerNo}>

<td>{student.registerNo}</td>

<td>{student.name}</td>

<td>{student.course}</td>

<td>{student.marks}</td>

</tr>

))}

</tbody>

</table>

)}

</div>

);

} 

export default App;//
student.json

[

{

"registerNo": "BCA001",

"name": "Arun",

"course": "BCA", Frontend Design Lab

MURALI M, NCJ

"marks": 85

},

{

"registerNo": "BCA002",

"name": "Priya",

"course": "BCA",

"marks": 90

},

{

"registerNo": "BCA003",

"name": "Rahul",

"course": "BCA",

"marks": 78

},

{

"registerNo": "BCA004",

"name": "Divya",

"course": "BCA",

"marks": 88

}

]

9. Convert a Static HTML Page into React Components (Using CDN)

a. Convert an existing HTML webpage into reusable React components using 

the React CDN.

b. Use React Props and the useState Hook to display dynamic data. Frontend Design Lab

MURALI M, NCJ

App.js

import React, { useState } from "react";

import "./App.css";

function Header() {

return <h1>Student Information</h1>;

}

function StudentCard(props) {

return (

<div className="card">

<h2>{props.name}</h2>

<p>Register No: {props.registerNo}</p>

<p>Course: {props.course}</p>

<p>Marks: {props.marks}</p>

</div>

);

}

function App() {

const [marks, setMarks] = useState(85);

const increaseMarks = () => {

setMarks(marks + 5); Frontend Design Lab

MURALI M, NCJ

};

return (

<div>

<Header />

<StudentCard

name="Arun"

registerNo="BCA001"

course="BCA"

marks={marks}

/>

<button onClick={increaseMarks}>

Increase Marks

</button>

</div>

);

}

export default App;
