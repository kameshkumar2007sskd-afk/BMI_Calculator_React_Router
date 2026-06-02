# Ex06 BMI Calculator
## Date: 02-06-2026
Name:S Kamesh Kumar
Reg No:212225220046
## AIM
To develop a responsive and interactive Body Mass Index (BMI) Calculator using React that allows users to input their height and weight, and calculates their BMI to categorize their health status (e.g., Underweight, Normal, Overweight, Obese).

## DESIGN STEPS

### STEP 1: Initialize React Project

<li>Create a new React app using create-react-app.</li>
<li>Install React Router using:</li>
npm install react-router-dom

### STEP 2: Set Up Routing

Create routing structure with react-router-dom:

<li>Home route (/) – Intro or Navigation</li>

<li>BMI Calculator route (/bmi)</li>

<li>Result route (/result)</li>

### STEP 3: Design the BMI Form Page

<li>Create a form to accept Height (in cm or m) and Weight (in kg).</li>

<li>On form submit, navigate to the result page with entered values via URL query params or context/state.</li>

## STEP 4: Handle Input Validation

<li>Check if height and weight are valid numbers.</li>

<li>Optionally, show error messages for invalid inputs.</li>

### STEP 5: Perform BMI Calculation

<li>In the result component:

<li>Extract height and weight from the route (URL or passed state).</li>

<li>Apply the BMI formula:</li>

![image](https://github.com/user-attachments/assets/ec785506-c96b-489e-8783-fb1a5d36101a)
​
 
<li>Convert height from cm to m if needed.</li></li>

### STEP 6: Display Result

<li>Show calculated BMI.</li>

<li>Show category based on BMI range:

<li>Underweight, Normal, Overweight, Obese, etc.</li></li>

### STEP 7: Navigation Options

<li>Provide a button to go back to the BMI form to calculate again.</li>

### STEP 8: Enhancements

<li>Add styling using CSS or Tailwind.</li>

## PROGRAM
App.jsx
```
import React, { useState } from 'react';
import './App.css';

function App() {
  const [weight, setWeight] = useState('');
  const [height, setHeight] = useState('');
  const [bmi, setBmi] = useState(null);
  const [message, setMessage] = useState('');

  const calculateBMI = () => {
    if (weight && height) {
      const heightInMeters = height / 100;
      const calculatedBMI = (weight / (heightInMeters * heightInMeters)).toFixed(2);
      setBmi(calculatedBMI);
      getBMICategory(calculatedBMI);
    } else {
      alert('Please enter valid height and weight.');
    }
  };

  const getBMICategory = (bmi) => {
    if (bmi < 18.5) setMessage('Underweight');
    else if (bmi >= 18.5 && bmi < 24.9) setMessage('Normal weight');
    else if (bmi >= 25 && bmi < 29.9) setMessage('Overweight');
    else setMessage('Obese');
  };

  const resetFields = () => {
    setWeight('');
    setHeight('');
    setBmi(null);
    setMessage('');
  };

  return (
    <div className="container">
      <h1>BMI Calculator</h1>
      <div className="input-group">
        <label>Weight (kg):</label>
        <input
          type="number"
          value={weight}
          onChange={(e) => setWeight(e.target.value)}
          placeholder="Enter weight"
        />
      </div>
      <div className="input-group">
        <label>Height (cm):</label>
        <input
          type="number"
          value={height}
          onChange={(e) => setHeight(e.target.value)}
          placeholder="Enter height"
        />
      </div>
      <button onClick={calculateBMI}>Calculate</button>
      <button className="reset" onClick={resetFields}>Reset</button>
      
      {bmi && (
        <div className="result">
          <h2>Your BMI: {bmi}</h2>
          <p className="message">{message}</p>
        </div>
      
      )}
    </div>
  );
}

export default App;
```
App.css
```
body {
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  background: linear-gradient(135deg, #fae0e0, #ffffff);
  margin: 0;
  padding: 0;
}

.container {
  max-width: 420px;
  margin: 80px auto;
  padding: 35px 25px;
  background-color: #ffffff;
  border-radius: 16px;
  box-shadow: 0 12px 24px rgba(0, 0, 0, 0.15);
  text-align: center;
  transition: transform 0.2s ease-in-out;
}

.container:hover {
  transform: translateY(-5px);
}

h1 {
  margin-bottom: 25px;
  font-size: 28px;
  color: #502c2c;
}

.input-group {
  margin-bottom: 20px;
  text-align: left;
}

.input-group label {
  display: block;
  margin-bottom: 6px;
  font-weight: 600;
  color: #5e3434;
}

.input-group input {
  width: 100%;
  padding: 12px;
  font-size: 16px;
  border: 2px solid #dfe6e9;
  border-radius: 10px;
  background-color: #f9f9f9;
  outline: none;
  transition: border-color 0.3s;
  box-sizing: border-box;
}

.input-group input:focus {
  border-color: #d40000;
}

button {
  padding: 12px 24px;
  font-size: 16px;
  margin: 12px 6px;
  border: none;
  border-radius: 10px;
  cursor: pointer;
  background-color: #d40000;
  color: white;
  transition: background-color 0.3s ease, transform 0.2s ease;
}

button:hover {
  background-color: #a70000;
  transform: scale(1.05);
}

button.reset {
  background-color: #a69595;
}

button.reset:hover {
  background-color: #8d7f7f;
}

.result {
  margin-top: 30px;
  padding: 20px;
  border-radius: 10px;
  background-color: #f1ecec;
  border-left: 5px solid #d40000;
  text-align: center;
}

.result h2 {
  margin-bottom: 10px;
  color: #502c2c;
}
.message {
  font-size: 18px;
  font-weight: bold;
  color: #502c2c;
}

footer {
  margin-top: 40px;
  font-size: 14px;
  color: #8d7f7f;
  font-weight: 500;
}
```

## OUTPUT
<img width="1600" height="942" alt="WhatsApp Image 2026-06-02 at 10 41 41 AM" src="https://github.com/user-attachments/assets/876b1a82-5e13-4194-87f3-f98b3c4892b7" />
<img width="1600" height="948" alt="WhatsApp Image 2026-06-02 at 10 42 00 AM" src="https://github.com/user-attachments/assets/2aa379fb-16ad-4695-ba43-b6dd9dc98815" />

## RESULT
The BMI Calculator successfully takes user input for height and weight, performs the BMI calculation in real-time using React state and event handling, and displays the BMI value along with the corresponding health category.
