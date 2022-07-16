In this project, we will create a web application COVID-19 Tracker using ReactJS and real-time API. In this web application, when we enters the name of the country, it will display the Country name, Cases, Deaths, Recovered.


#### Pre-requisites:

Basic JavaScript such as functions, types of variables, objects, etc.
ReactJS development setup for web development.
ReactJS Hooks such as useState Hook and useEffect Hook.
APIs knowledge to fetch real-time data.
Basic CSS properties for styling and designing for the web application.


#### Approach:

Set up the development environment, install all the required dependencies.
In the App.js file, create and initialise a component that is used to hold the code of the web application.
In that JavaScript file, create a form to take the input from the user and fetch and display the details using real-time API and react useState Hook and useEffect Hook.
Use CSS for stylings of the component file and import the CSS file in the component file.


Below is the step by the step implementation of the above approach:

**Step 1:** Create a React application using the following command:
        npx create-react-app covid-19-tracker-in-react

**Step 2:** After creating our project folder i.e.covid-19-tracker-in-react, move to it using the following command:
        cd covid-19-tracker-in-react

In that created folder go to src folder and delete App.test.js, logo.svg and setupTests.js because these files are not required in this project and add component files used to hold the code for the application. Our component name is CovidData and file name is CovidData.js and for stylings add CSS file CovidData.css.

**Project Structure:** It will look like the following:

- node_modules
- public
- src
  - App.css
  - App.js
  - CovidData.css
  - CovidData.js
  - index.js
 - reportWebVitals.js
- .gitignore
- {} package-lock.json
- {} package.json
- README.md


**Step 3:** Now, in App.js, we will create the component file, that will hold the code for the application.

### App.js
```
import "./App.css";
import CovidData from "./CovidData";
  
function App() {
  return <div className="App">
    <CovidData/>
  </div>;
}
  
export default App;
```

Our component name is CovidData and we have imported this component file in App.js.

**Step 4:** In the CovidData.js file, we will create the form to take the input and when the form is submitted then it will fetch the data from the API with the help of useEffect Hook and set the fetched data in the variable objects using useState Hook. When the data is fetched then pass the variable objects using JSX expression to display the data. To get data, real-time API we have used the “https://disease.sh/v3/covid-19/countries” API.

### CovidData.js

```
import React, { useEffect, useState } from "react";
import "./CovidData.css";
  
function CovidData() {
  const [country, setCountry] = useState("");
  const [cases, setCases] = useState("");
  const [recovered, setRecovered] = useState("");
  const [deaths, setDeaths] = useState("");
  
  useEffect(() => {
    fetch("https://disease.sh/v3/covid-19/countries")
      .then((res) => res.json())
      .then((data) => {
        setData(data);
      });
  }, []);
  
  const setData = ({
    country,
    cases,
    deaths,
    recovered
  }) => {
    setCountry(country);
    setCases(cases);
    setRecovered(recovered);
    setDeaths(deaths);
  };
  
  const handleSearch = (e) => {
    setUserInput(e.target.value);
  };
  const handleSubmit = (props) => {
    props.preventDefault();
    fetch(`https://disease.sh/v3/covid-19/countries/${userInput}`)
      .then((res) => res.json())
      .then((data) => {
        setData(data);
      });
  };
  
  return (
    <div className="covidData">
      <h1>COVID-19 CASES COUNTRY WISE</h1>
      <div className="covidData__input">
        <form onSubmit={handleSubmit}>
          {/* input country name */}
          <input onChange={handleSearch} placeholder="Enter Country Name" />
          <br />
          <button type="submit">Search</button>
        </form>
      </div>
  
      {/* Showing the details of the country */}
      
		<div className="country"><h3 className="title1">Country Name</h3> <span className="data"> {country} </span></div>

		<div className="cases"><h3 className="title2">Cases </h3><span className="data">{cases}</span></div>

		<div className="death"><h3 className="title3">Deaths </h3><span className="data"> {deaths}</span></div>

		<div className="recovered"><h3 className="title4">Recovered</h3><span className="data">{recovered}</span></div>
        </div>
);
}

export default CovidData;
```
      
**Step 5:** For stylings, we have used basic CSS properties such as alignment, font style, etc.

### CovidData.css

```
body {
    background-color: rgb(83, 237, 206);
    }
    .covidData {
    background-color: rgb(58, 143, 133);
    height: 90vh;
    width: 50%;
    margin: auto;
    margin-top: 15px;
    border-radius: 6px;
    padding: 10px;
    }
    
    /* input stylings */
    
    .covidData__form {
    padding: 10px;
    margin: 20px;
    }
    .covidData__input input {
    width: 400px;
    height: 35px;
    text-align: center;
    font-size: 20px;
    border-radius: 10px;
    text-decoration: none;
    font-family: Verdana, Geneva, Tahoma, sans-serif;
    outline: none;
    }
    .covidData__input button {
    width: 100px;
    height: 40px;
    position: relative;
    top: 10px;
    margin-top: 10px;
    background-color: black;
    color: white;
    font-size: 20px;
    border-radius: 10px;
    border: none;
    box-shadow: 2px 5px 10px rgb(71, 67, 67);
    cursor: pointer;
    }
    
    /* detail stylings */
    

    .country {
    font-size: 20px;
    
    font-family: Verdana, Geneva, Tahoma, sans-serif;
    width: 200px;
    margin-left: auto;
    margin-right: auto;
    height: 150px;
    position: relative;
    top: 25px;
    left: -125px;
    padding-left: 10px;
    background-color: white;
    border-radius: 7px;
    margin-top: 20px;
    padding: 2px;
    text-shadow: 0px 1px 2px rgb(71, 67, 67);
    box-shadow: 5px 5px 5px rgb(71, 67, 67);

    }
    .cases {
    font-size: 20px;
    font-family: Verdana, Geneva, Tahoma, sans-serif;
    width: 200px;
    margin-left: auto;
    margin-right: auto;
    height: 150px;
    position: relative;
    top: -147px;
    left: 125px;
    padding-left: 10px;
    background-color: white;
    border-radius: 7px;
    margin-top: 20px;
    padding: 2px;
    text-shadow: 0px 1px 2px rgb(71, 67, 67);
    box-shadow: 5px 5px 5px rgb(71, 67, 67);
    }
    .death {
    font-size: 20px;
    font-family: Verdana, Geneva, Tahoma, sans-serif;
    width: 200px;
    margin-left: auto;
    margin-right: auto;
    height: 150px;
    position: relative;
    top: -110px;
    left: -125px;
    padding-left: 10px;
    background-color: white;
    border-radius: 7px;
    margin-top: 20px;
    padding: 2px;
    text-shadow: 0px 1px 2px rgb(71, 67, 67);
    box-shadow: 5px 5px 5px rgb(71, 67, 67);
    }
    .recovered {
    font-size: 20px;
    font-family: Verdana, Geneva, Tahoma, sans-serif;
    width: 200px;
    margin-left: auto;
    margin-right: auto;
    height: 150px;
    position: relative;
    top: -282px;
    left: 125px;
    padding-left: 10px;
    background-color: white;
    border-radius: 7px;
    margin-top: 20px;
    padding: 2px;
    text-shadow: 0px 1px 2px rgb(71, 67, 67);
    box-shadow: 5px 5px 5px rgb(71, 67, 67);
    }
  .title1{
      color: blue;
      font-size:x-large;
      font-family:fangsong ;
  }
  .title2{
      color: red;
      font-size:x-large;
      font-family:fangsong ;
  }
  .title3{
      color: #ff9800;
      font-size:x-large;
      font-family:fangsong ;
  }
  .title4{
      color: #054c05;
      font-size:x-large;
      font-family:fangsong ;
  }
  .data{
      position: relative;
      top:4px;
  }
```

**Step to Run Application:** Run the application using the following command from the root directory of the project:

npm start

**Output:** Now open your browser and go to http://localhost:3000/, you will see the output
