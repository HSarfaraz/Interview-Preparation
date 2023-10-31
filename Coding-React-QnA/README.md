## React Coding interview questions

<i size="8px">from youtube --> Cybernatico 5 hours<i>

<br/>
<hr/>
<br/>

### Chapter 1:

```javascript
//Question 1: Map and Filter Example

import React, { useEffect, useState } from "react";

const OneMapnFilter = () => {
  const [users, setUsers] = useState([]);
  const [numbers, setNumbers] = useState([1, 2, 3, 4, 5, 6, 7, 8, 9, 10]);

  //calling an api
  useEffect(() => {
    let url = "https://jsonplaceholder.typicode.com/users";
    fetch(url)
      .then((response) => response.json())
      .then((userdata) => setUsers(userdata));
    console.log(users);
  }, []);

  //we want to multiply user by 2
  /* const mapData = () => {
		let mappedArray = users.map(user => user.id * 2)
		console.log(mappedArray);
	} */

  //using filter: filter the data which has name A
  /* const mapData = ()=>{
		let filteredData = users.filter(user=>{
			// return user.name === "Leanne Graham";
			// return user.name.includes("C"); 
			return user.id <= 5;
		});
		console.log(filteredData);
	} */

  //Example 3:
  /* const mapData = ()=>{
		let filteredData = users.filter(user=>{
			return user.id > 5;
		})
		setUsers(filteredData)
	} */

  //Example 4: map with filter
  //square the number
  /* const mapData = ()=>{
		let square = numbers.map(number=>{
			return number * number
		})
		setNumbers(square);
	} */

  //number less than 5
  /* const mapData = ()=>{
		let numberLessFive = numbers.filter(number=>{
			return number > 5
		}).map(filtered=>{
			return filtered * filtered;
		})
		setNumbers(numberLessFive);
	} */

  const mapData = () => {
    let numberLessFity = numbers
      .map((number) => {
        return number * number;
      })
      .filter((filtered) => {
        return filtered > 50;
      });
    setNumbers(numberLessFity);
  };

  return (
    <div className="App">
      {/* <h1>Users</h1>
			<div className="">
				{users.map((user) => (
					<div className="card mx-auto mr-2 d-inline-flex w-10 p-2 m-2 bg-light" key={user.id}>
						<div className="card-body">
							<p className="card-text">{user.name}</p>
							<p className="card-text">{user.username}</p>
						</div>
					</div>
				))
			} 
			</div>
			*/}

      {/* Map the numbers */}
      <div>
        <h1>Numbers</h1>
        {numbers.map((number) => (
          <div key={number} className="card">
            {number}
          </div>
        ))}
      </div>

      <button onClick={mapData} className="btn btn-secondary">
        See mapped Array
      </button>
    </div>
  );
};

export default OneMapnFilter;
```

<br/>
<hr/>
<br/>

### Chapter 2:

/_ Question 2:_/

```javascript
/*using function*/
import React, { useState } from "react";

const TwoStates = () => {
  const [count, setCount] = useState(0);
  const [name, setName] = useState("");
  const [isVisible, setIsVisible] = useState(false);
  const [array, setArray] = useState([
    {
      name: "Sarfaraz",
      age: 38
    },
    {
      name: "Kamran",
      age: 32
    }
  ]);

  const increment = () => {
    setCount(count + 1);
    setIsVisible(!isVisible);
    setName("Sarfaraz");
  };

  const [object, setObjects] = useState({ name: "Sarfaraz", age: 37 });
  return (
    <div>
      <h1>{count}</h1>
      <h1>{name}</h1>
      {isVisible ? <h1>Visible</h1> : <h1>Not visible</h1>}
      <button onClick={increment}>Increment the button</button>
    </div>
  );
};

export default TwoStates;
```

```javascript
/*using class*/
import React, { Component } from "react";

export default class TwoStateClass extends Component {
  constructor() {
    super();
    //create the state
    this.state = {
      name: "Sarfaraz",
      age: 37,
      arr: [1, 2, 3, 4, 5, 6]
    };
  }

  //how class works
  changeStatus = () => {
    this.setState({ age: this.state.age * 2, name: "Kamran" });
  };

  render() {
    return (
      <div>
        <h1>{this.state.name}</h1>
        <h1>{this.state.age}</h1>
        {this.state.arr.map((item) => (
          <h3>{item}</h3>
        ))}
        <button onClick={this.changeStatus}>Change status</button>
      </div>
    );
  }
}
```

<br/>
<hr/>
<br/>

### Chapter 3: Passing data from child to parent

<!-- Question 3 -->

```javascript
//Question 3:
import React, { useState } from "react";
import ThreeChild from "./ThreeChild";

const ThreeProps = () => {
  const [name, setName] = useState("Sarfaraz");
  //value is passed from child to parent
  const changeName = (value) => {
    setName(value);
  };

  return (
    <div>
      <ThreeChild valueOfProp={name} changeName={changeName} />
    </div>
  );
};

export default ThreeProps;
```

```javascript
import React from "react";

const ThreeChild = ({ valueOfProp, changeName }) => {
  return (
    <div>
      <h3>{valueOfProp}</h3>

      <button onClick={() => changeName("This name is from child")}>
        Change Name
      </button>
    </div>
  );
};

export default ThreeChild;
```

<br/>
<hr/>
<br/>

### Chapter 4: Inline Condition

```javascript
//
import React, { useEffect } from "react";

const FourInlineCondition = () => {
  let age = 28;
  let name = "Sarfaraz";
  useEffect(() => {
    /* if(age>26){
			console.log("you are now old");
		}else if(name == "Sarfaraz" && age === 26){
			console.log("I am 26 year old");
			console.log("Sarfaraz is my name");
		}else{
			console.log("Sarfaraz is not my name");
			console.log("I am less than 26 year old");
		} */

    age > 26 ? (
      console.log("you are now old")
    ) : name == "Sarfaraz" || age === 26 ? (
      <>
        {console.log("I am 26 year old")}
        {console.log("Sarfaraz is my name")}
      </>
    ) : (
      <>
        {console.log("Sarfaraz is not my name")}
        {console.log("I am less than 26 year old")}
      </>
    );
  }, []);

  return (
    <div>
      {age > 26 ? (
        <h1>you are now old </h1>
      ) : name == "Sarfaraz" || age === 26 ? (
        <>
          <h1> I am 26 year old </h1>
          <h1> Sarfaraz is my name </h1>
        </>
      ) : (
        <>
          <h1>Sarfaraz is not my name </h1>
          <h1>I am less than 26 year old </h1>
        </>
      )}
    </div>
  );
};

export default FourInlineCondition;
```

<br/>
<hr/>
<br/>

### Chapter 5: Event Handling

```javascript
import React from "react";

export const FiveEventHandling = () => {
  const getInputs = (event) => {
    //to get the name
    console.log(event.target.name);
  };

  const addNums = (num1, num2) => {
    console.log(num1 + num2);
  };

  return (
    <div>
      <input
        placeholder="Add something.."
        onChange={getInputs}
        name="input"
      ></input>
      <button onClick={() => addNums(2, 2)}>Add numbers</button>
    </div>
  );
};
```

<br/>
<hr/>
<br/>

### Chapter 6:  Keys

```javascript
import React from "react";

const SixKeys = () => {
  const numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
  const details = [
    {
      name: "Dinesh Karthik",
      age: 37
    },
    {
      name: "KL Rhul",
      age: 30
    },
    {
      name: "Rishab Panth",
      age: 25
    },
    {
      name: "Md. Siraj",
      age: 29
    }
  ];

  const numbersList = numbers.map((number, index) => {
    return <li key={index}>{number}</li>;
  });
  const detailsList = details.map((value, index) => {
    return (
      <span key={index}>
        <li>{value.name}</li>
        <li>{value.age}</li>
      </span>
    );
  });
  return (
    <div>
      <ul>{numbersList}</ul>
      <ul>{detailsList}</ul>
    </div>
  );
};

export default SixKeys;
```

<br/>
<hr/>
<br/>

### Chapter 7:

```javascript
import React, { useState } from "react";

const SevenForms = () => {
  //create the object state to store the all values
  const [objData, setObjData] = useState({});

  const getInputs = (value, name) => {
    //print the details like key value pair
    // console.log( [name], value);

    //merging the data using key, value pair
    let data = { [name]: value };
    setObjData({ ...objData, ...data }); //here. ...objData is previous data or olda data, ...data is new data.
    console.log(objData);
  };

  //Submit the data
  const submit = (event) => {
    event.preventDefault(); // to avoid refresh the page
    console.log(objData);
  };

  return (
    <form className="form" onSubmit={submit}>
      <input
        placeholder="Write your name"
        name="name"
        type="text"
        onChange={(event) => getInputs(event.target.value, event.target.name)}
      />{" "}
      <br />
      <br />
      <input
        placeholder="Write your age"
        name="age"
        type="number"
        onChange={(event) => getInputs(event.target.value, event.target.name)}
      />{" "}
      <br />
      <br />
      <input
        placeholder="Write your hobbies"
        name="hobbies"
        type="text"
        onChange={(event) => getInputs(event.target.value, event.target.name)}
      />{" "}
      <br />
      <br />
      <input
        placeholder="Write a Date"
        name="date"
        type="date"
        onChange={(event) => getInputs(event.target.value, event.target.name)}
      />{" "}
      <br />
      <br />
      <button type="submit">Submit</button>
      <button type="reset">Reset</button>
    </form>
  );
};

export default SevenForms;
```

<br/>
<hr/>
<br/>

### Chapter 8:

```javascript
import React, { useState } from "react";

const EightDynamicInput = () => {
  const [inputs, setInputs] = useState({});

  const getInputValues = (data) => {
    // console.log(data.target.name);
    let { name, value } = data.target;
    let input = { [name]: value };
    setInputs({ ...inputs, ...input }); //here. inputs is the old data, ...input is the current data, so we are merging it.
  };

  const sendDataToAPI = () => {
    console.log(inputs);
  };

  return (
    <div className="App">
      <div className="input-container">
        <input placeholder="Name" name="name" onChange={getInputValues} />
        <input placeholder="Age" name="age" onChange={getInputValues} />
        <input
          placeholder="Years of experience"
          name="yoe"
          onChange={getInputValues}
        />
      </div>
      <button onClick={sendDataToAPI}>Add new Group</button>
    </div>
  );
};

export default EightDynamicInput;
```

<br/>
<hr/>
<br/>

### Chapter 9:

```javascript
import React, { useState } from "react";

const NineCSSStyle = () => {
  const [theme, setTheme] = useState(false);

  /* This internal stylying */
  const styles = {
    internal: {
      color: "blue"
    },
    light: {
      backgroundColor: "white",
      color: "black"
    },
    dark: {
      backgroundColor: "black",
      color: "white"
    }
  };

  const ToggleTheme = () => {
    setTheme(!theme);
  };

  return (
    <div style={theme ? styles.light : styles.dark}>
      <h1 className="external"> External styling</h1>

      <h1 style={styles.internal}>Internal styling</h1>

      {/* <h1 style={{color:"green", backgroundColor:'black'}}>Inline styling</h1> */}

      {/* If theme is light then show the light theme else show dark theme */}
      <h1
        style={
          theme
            ? { color: "black", backgroundColor: "white" }
            : { color: "white", backgroundColor: "black" }
        }
      >
        Inline styling
      </h1>

      <button onClick={ToggleTheme}>Toggle theme</button>
    </div>
  );
};

export default NineCSSStyle;
```

<br/>
<hr/>
<br/>

### Chapter 10:

```javascript
import React, { createRef } from "react";

/* Notes:
Uncontrolled Component: 
-	we are controlling the component using DOM using reference value.
-	We cant update the values automatically

Controlled Component:
- we are controlling the component using react.
- Here our component is getting refreshed
*/
const TenControlledVsUncontrolled = () => {
  // For Uncontrolled component
  //create the reference for name, age
  /* let name = createRef();
	let age = createRef();	
	const submit = ()=>{
		console.log(name.current.value);
		console.log(age.current.value);
	} */

  const getName = (event) => {
    console.log(event.target.value);
  };

  return (
    <div className="App">
      {/* Uncontrolled component */}
      {/* <>
			<input placeholder="name" ref={name}/>
			<input placeholder='age' ref={age}/>
			<button onClick={submit}>Submit</button>
			</> */}

      {/* Controlled component */}
      <>
        <input placeholder="name" onChange={getName} />
        <input placeholder="age" />
        <button>Submit</button>
      </>
    </div>
  );
};

export default TenControlledVsUncontrolled;
```

<br/>
<hr/>
<br/>

### Chapter 11:

```javascript
// App
import Family from "./Family";
import { familyTree } from "./data";

const RecursionApp = () => {
  return (
    <div>
      <Family familyTree={familyTree} /> {/* Step 1*/}
    </div>
  );
};

export default RecursionApp;
```

```javascript
import React, { useState } from "react";

{
  /* Step 2*/
}
const Family = ({ familyTree }) => {
  const [isVisible, setIsVisible] = useState(false);

  const expand = () => {
    setIsVisible(!isVisible);
  };

  return (
    <div style={{ paddingLeft: 10 }}>
      <span onClick={expand}>{familyTree.name}</span>

      {isVisible ? (
        familyTree?.children?.map((child) => {
          return (
            <div style={{ paddingLeft: 10 }}>
              {/* <span>{child.name}</span> */}
              <Family familyTree={child} />
              {/* Step 4: This is recursion*/}
            </div>
          );
        })
      ) : (
        <></>
      )}
    </div>
  );
};

export default Family;
```

```javascript
{
  /* Step 3*/
}
export const familyTree = {
  name: "John",
  age: 90,
  children: [
    {
      name: "Mary",
      age: 60
    },
    {
      name: "Arthur",
      age: 60,
      children: [
        {
          name: "Lily",
          age: 35,
          children: [
            {
              name: "Hank",
              age: 60
            },
            {
              name: "Henry",
              age: 57
            }
          ]
        },
        {
          name: "Billy",
          age: 37
        }
      ]
    },
    {
      name: "Dolores",
      age: 55
    }
  ]
};
```

<br/>
<hr/>
<br/>

### Chapter 12:

```javascript
import React, { useState } from "react";
import ReactQuill from "react-quill";
import "react-quill/dist/quill.snow.css";

// Install react-quill": npm install react-quill

const TweleveInnerHTML = () => {
  const [quilltext, setQuillText] = useState();
  // This p tag is html
  let data = `<p style="font-size: 20px; color: red">This is p tage</p>`;
  let data2 = `<b style="font-size: 20px; color: "blue">This is my Home</b>`;

  const getQuillData = (value) => {
    setQuillText(value);
  };

  console.log(quilltext);

  return (
    <div>
      {/* The below will print the content with p tag */}
      {/* {data} */}

      {/* To have smooth display, we use dangerouslySetInnetHTML tag */}
      <div dangerouslySetInnerHTML={{ __html: data }}></div>
      <div dangerouslySetInnerHTML={{ __html: data2 }}></div>

      {/* This is JSX*/}
      <p style={{ fontSize: "20px", color: "red" }}>This is my Home</p>

      {/* Display the data for quill */}
      <div dangerouslySetInnerHTML={{ __html: quilltext }}></div>

      {/*  value={text} onChange={handleChange} */}
      <ReactQuill value={quilltext} onChange={getQuillData} />
    </div>
  );
};

export default TweleveInnerHTML;
```

<br/>
<hr/>
<br/>

### Chapter 13:

```javascript
import React, { Fragment } from "react";

const ThirteenFragment = () => {
  return (
    <Fragment>
      <>
        <h1>Hello wordl</h1>
      </>
      <>
        <h1>Hello</h1>
        <h1> World </h1>
      </>
    </Fragment>
  );
};

export default ThirteenFragment;
```

<br/>
<hr/>
<br/>

### Chapter 14:

```javascript
import React, { useState } from "react";

const FourteenStatelessVSStateful = () => {
  const [name, setName] = useState("Sarfaraz");
  return (
    <div>
      <h1>{name}</h1>
    </div>
  );
};

export default FourteenStatelessVSStateful;
```

<br/>
<hr/>
<br/>

### Chapter 15:

```javascript
import React, { useState, useEffect } from "react";
import axios from "axios";

const FifteenCRUD = () => {
  const [name, setName] = useState("");
  const [users, setUsers] = useState([]);

  const url = "https://64b8a52221b9aa6eb07a0498.mockapi.io/APIendpoint";

  //POST request
  const postData = () => {
    axios
      .post(url, {
        name: name,
        age: 37,
        hobbies: [
          "cricket",
          "poetry",
          "cooking",
          "travelling",
          "coding",
          "Piano"
        ]
      })
      .then((response) => {
        setUsers([response.data]); // Wrap the response data in an array
      })
      .catch((error) => {
        setUsers([error]); // Wrap the error object in an array
      });
  };

  const getData = () => {
    axios
      .get(url)
      .then((response) => {
        setUsers(response.data); // Set the response data directly
      })
      .catch((error) => {
        setUsers([error]); // Wrap the error object in an array
      });
  };
  //GET request
  useEffect(() => {
    getData();
  }, []);

  //PUT request
  const updateData = (id) => {
    // console.log(id);
    axios
      .put(`https://64b8a52221b9aa6eb07a0498.mockapi.io/APIendpoint/${id}`, {
        name: name,
        age: 31,
        hobbies: [
          "cricket",
          "poetry",
          "cooking",
          "travelling",
          "coding",
          "Piano",
          "football",
          "rugby"
        ]
      })
      .then((response) => console.log(response.data))
      .catch((err) => console.log(err));
  };

  //DELETE request
  const deleteData = (id) => {
    axios
      .delete(`https://64b8a52221b9aa6eb07a0498.mockapi.io/APIendpoint/${id}`)
      .then((response) => getData())
      .catch((err) => console.log(err));
  };

  return (
    <div>
      <button onClick={postData}>POST Data</button>
      <input
        placeholder="name"
        onChange={(event) => setName(event.target.value)}
      />

      {Array.isArray(users) &&
        users.map((user) => (
          <ul key={user.id}>
            <>
              <h2>{`${user.id}. ${user.name}`}</h2>
              <button onClick={() => updateData(user.id)}>Update</button>
              <button onClick={() => deleteData(user.id)}>Delete</button>

              {/* Access the name property directly */}
            </>
          </ul>
        ))}
    </div>
  );
};

export default FifteenCRUD;
```

<br/>
<hr/>
<br/>

### Chapter 16:

```javascript
import React, { useEffect, useState } from "react";
import axios from "axios";

/*Notes:

-	simple means delay a function

-	Debouncing is a programming technique that helps 
to improve the performance of web applications by limiting the frequency of function calls.

-	Reference: https://www.freecodecamp.org/news/javascript-debounce-example/

- In Debouncing the API call happens only once.
-	
*/

const pinAPI = `https://api.postalpincode.in/pincode/`;

const SixteenDebouncing = () => {
  const [pin, setPin] = useState("");

  const searchPin = (pin) => {
    axios
      .get(pinAPI + pin)
      .then((response) => console.log(response.data))
      .catch((err) => console.log(err));
  };

  useEffect(() => {
    const debouncing = setTimeout(() => {
      searchPin(pin);
    }, 2000);
    return () => {
      clearTimeout(debouncing);
    };
  }, [pin]);

  return (
    <div>
      <input
        type="text"
        name="pincode"
        placeholder="Enter pincode details"
        onChange={(event) => setPin(event.target.value)}
        className="fonrm-control"
      />
    </div>
  );
};

export default SixteenDebouncing;
```

<br/>
<hr/>
<br/>

### Chapter 17: Context API

```javascript
//App
import React, { useState } from "react";
import Home from "./Home";
import Profile from "./Profile";
import { UserData } from "./GlobalContext"; //Step2: importing the context

const ContextAPI = () => {
  const [name, setName] = useState("Sarfaraz");
  const [age, setAge] = useState(37);

  return (
    <div>
      {/* Step 3: Providing the context */}
      <UserData.Provider value={{ name, setName, age }}>
        <Home />
        <Profile />
      </UserData.Provider>
    </div>
  );
};

export default ContextAPI;
```

```javascript
import { createContext } from "react";

//Step 1: Creating the context
export const UserData = createContext({});
```

```javascript
import React, { useContext } from "react";
import { UserData } from "./GlobalContext";

const Profile = () => {
  let { setName } = useContext(UserData);
  return (
    <div>
      <button onClick={() => setName("Kamran")}>Change Name</button>
    </div>
  );
};

export default Profile;
```

```javascript
import React from "react";
import { useContext } from "react";
import { UserData } from "./GlobalContext";
import Settings from "./Settings";

const Home = () => {
  //Step4: Consuming the context
  //destructure it
  let { name } = useContext(UserData);

  return (
    <div>
      Home {name}
      <Settings />
    </div>
  );
};

export default Home;
```

```javascript
import React, { useContext } from "react";
import { UserData } from "./GlobalContext";

const Settings = () => {
  let { age } = useContext(UserData);
  return <div>Settings {age}</div>;
};

export default Settings;
```

<br/>
<hr/>
<br/>

### Chapter 18:  Higher order component

```javascript
import React, { useEffect, useState } from "react";

const HigherOrder = (title, Component, request) => {
  return function HOC() {
    const [data, setData] = useState([]);

    const getData = async () => {
      let data = await fetch(`https://jsonplaceholder.typicode.com/${request}`)
        .then((response) => response)
        .catch((err) => err);

      setData(await data.json());
    };

    useEffect(() => {
      getData();
    }, []);

    return (
      <div>
        <h2>{title}</h2>
        <Component data={data} />
      </div>
    );
  };
};

export default HigherOrder;
```

```javascript
import React from "react";
import Users from "./Users";
import Posts from "./Posts";

const Myindex = () => {
  return (
    <div>
      <Users />
      <Posts />
    </div>
  );
};

export default Myindex;
```

```javascript
import React, { useEffect, useState } from "react";
import HigherOrder from "./HigherOrder";

const Posts = ({ data }) => {
  return (
    <div>
      <h3>Hello from Posts</h3>
      {data.slice(0, 10).map((post) => {
        return <p>{post.title}</p>;
      })}
    </div>
  );
};

const PostsComp = HigherOrder("Posts", Posts, "posts");
export default PostsComp;
```

```javascript
import React, { useEffect, useState } from "react";
import HigherOrder from "./HigherOrder";

const Users = ({ data }) => {
  return (
    <div>
      <h3>Hello from Users</h3>
      {data.slice(0, 10).map((user) => {
        return <p>{user.name}</p>;
      })}
    </div>
  );
};

const UsersComp = HigherOrder("Users", Users, "users");

export default UsersComp;
```

<br/>
<hr/>
<br/>

### Chapter 19: Lazing Loading, Suspense

```javascript
// App
import React, { lazy, Suspense } from "react";
import Home from "./Home";
import Lorem from "./Lorem";

const LoremLazy = lazy(() => import("./Lorem"));
const HomeLazy = lazy(() => import("./Home"));

const Loader = () => {
  <div>
    <h1>Loading... please wait</h1>
  </div>;
};

const LazyloadingApp = () => {
  return (
    <div>
      <Suspense fallback={<Loader />}>
        <HomeLazy />
        <LoremLazy />
      </Suspense>
      {/* <Home />
			<Lorem /> */}
    </div>
  );
};

export default LazyloadingApp;
```

```javascript
import React from "react";

const Lorem = () => {
  return (
    <div>
      What is Lorem Ipsum? Lorem Ipsum is simply dummy text of the printing and
      typesetting industry. Lorem Ipsum has been the industry's standard dummy
      text ever since the 1500s, when an unknown printer took a galley of type
      and scrambled it to make a type specimen book. It has survived not only
      five centuries, but also the leap into electronic typesetting, remaining
      essentially unchanged. It was popularised in the 1960s with the release of
      Letraset sheets containing Lorem Ipsum passages, and more recently with
      desktop publishing software like Aldus PageMaker including versions of
      Lorem Ipsum. Why do we use it? It is a long established fact that a reader
      will be distracted by the readable content of a page when looking at its
      layout. The point of using Lorem Ipsum is that it has a more-or-less
      normal distribution of letters, as opposed to using 'Content here, content
      here', making it look like readable English. Many desktop publishing
      packages and web page editors now use Lorem Ipsum as their default model
      text, and a search for 'lorem ipsum' will uncover many web sites still in
      their infancy. Various versions have evolved over the years, sometimes by
      accident, sometimes on purpose (injected humour and the like). Where does
      it come from? Contrary to popular belief, Lorem Ipsum is not simply random
      text. It has roots in a piece of classical Latin literature from 45 BC,
      making it over 2000 years old. Richard McClintock, a Latin professor at
      Hampden-Sydney College in Virginia, looked up one of the more obscure
      Latin words, consectetur, from a Lorem Ipsum passage, and going through
      the cites of the word in classical literature, discovered the undoubtable
      source. Lorem Ipsum comes from sections 1.10.32 and 1.10.33 of "de Finibus
      Bonorum et Malorum" (The Extremes of Good and Evil) by Cicero, written in
      45 BC. This book is a treatise on the theory of ethics, very popular
      during the Renaissance. The first line of Lorem Ipsum, "Lorem ipsum dolor
      sit amet..", comes from a line in section 1.10.32. The standard chunk of
      Lorem Ipsum used since the 1500s is reproduced below for those interested.
      Sections 1.10.32 and 1.10.33 from "de Finibus Bonorum et Malorum" by
      Cicero are also reproduced in their exact original form, accompanied by
      English versions from the 1914 translation by H. Rackham. Where can I get
      some? There are many variations of passages of Lorem Ipsum available, but
      the majority have suffered alteration in some form, by injected humour, or
      randomised words which don't look even slightly believable. If you are
      going to use a passage of Lorem Ipsum, you need to be sure there isn't
      anything embarrassing hidden in the middle of text. All the Lorem Ipsum
      generators on the Internet tend to repeat predefined chunks as necessary,
      making this the first true generator on the Internet. It uses a dictionary
      of over 200 Latin words, combined with a handful of model sentence
      structures, to generate Lorem Ipsum which looks reasonable. The generated
      Lorem Ipsum is therefore always free from repetition, injected humour, or
      non-characteristic words etc. 5 paragraphs words bytes lists Start with
      'Lorem ipsum dolor sit amet...' Translations: Can you help translate this
      site into a foreign language ? Please email us with details if you can
      help. There is a set of mock banners available here in three colours and
      in a range of standard banner sizes: BannersBannersBanners Donate: If you
      use this site regularly and would like to help keep the site on the
      Internet, please consider donating a small sum to help pay for the hosting
      and bandwidth bill. There is no minimum donation, any sum is appreciated -
      click here to donate using PayPal. Thank you for your support. Donate
      Bitcoin: 16UQLq1HZ3CNwhvgrarV6pMoA2CDjb4tyF NodeJS Python Interface GTK
      Lipsum Rails .NET Groovy The standard Lorem Ipsum passage, used since the
      1500s "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do
      eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad
      minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex
      ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate
      velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat
      cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id
      est laborum." Section 1.10.32 of "de Finibus Bonorum et Malorum", written
      by Cicero in 45 BC "Sed ut perspiciatis unde omnis iste natus error sit
      voluptatem accusantium doloremque laudantium, totam rem aperiam, eaque
      ipsa quae ab illo inventore veritatis et quasi architecto beatae vitae
      dicta sunt explicabo. Nemo enim ipsam voluptatem quia voluptas sit
      aspernatur aut odit aut fugit, sed quia consequuntur magni dolores eos qui
      ratione voluptatem sequi nesciunt. Neque porro quisquam est, qui dolorem
      ipsum quia dolor sit amet, consectetur, adipisci velit, sed quia non
      numquam eius modi tempora incidunt ut labore et dolore magnam aliquam
      quaerat voluptatem. Ut enim ad minima veniam, quis nostrum exercitationem
      ullam corporis suscipit laboriosam, nisi ut aliquid ex ea commodi
      consequatur? Quis autem vel eum iure reprehenderit qui in ea voluptate
      velit esse quam nihil molestiae consequatur, vel illum qui dolorem eum
      fugiat quo voluptas nulla pariatur?" 1914 translation by H. Rackham "But I
      must explain to you how all this mistaken idea of denouncing pleasure and
      praising pain was born and I will give you a complete account of the
      system, and expound the actual teachings of the great explorer of the
      truth, the master-builder of human happiness. No one rejects, dislikes, or
      avoids pleasure itself, because it is pleasure, but because those who do
      not know how to pursue pleasure rationally encounter consequences that are
      extremely painful. Nor again is there anyone who loves or pursues or
      desires to obtain pain of itself, because it is pain, but because
      occasionally circumstances occur in which toil and pain can procure him
      some great pleasure. To take a trivial example, which of us ever
      undertakes laborious physical exercise, except to obtain some advantage
      from it? But who has any right to find fault with a man who chooses to
      enjoy a pleasure that has no annoying consequences, or one who avoids a
      pain that produces no resultant pleasure?" Section 1.10.33 of "de Finibus
      Bonorum et Malorum", written by Cicero in 45 BC "At vero eos et accusamus
      et iusto odio dignissimos ducimus qui blanditiis praesentium voluptatum
      deleniti atque corrupti quos dolores et quas molestias excepturi sint
      occaecati cupiditate non provident, similique sunt in culpa qui officia
      deserunt mollitia animi, id est laborum et dolorum fuga. Et harum quidem
      rerum facilis est et expedita distinctio. Nam libero tempore, cum soluta
      nobis est eligendi optio cumque nihil impedit quo minus id quod maxime
      placeat facere possimus, omnis voluptas assumenda est, omnis dolor
      repellendus. Temporibus autem quibusdam et aut officiis debitis aut rerum
      necessitatibus saepe eveniet ut et voluptates repudiandae sint et
      molestiae non recusandae. Itaque earum rerum hic tenetur a sapiente
      delectus, ut aut reiciendis voluptatibus maiores alias consequatur aut
      perferendis doloribus asperiores repellat." 1914 translation by H. Rackham
      "On the other hand, we denounce with righteous indignation and dislike men
      who are so beguiled and demoralized by the charms of pleasure of the
      moment, so blinded by desire, that they cannot foresee the pain and
      trouble that are bound to ensue; and equal blame belongs to those who fail
      in their duty through weakness of will, which is the same as saying
      through shrinking from toil and pain. These cases are perfectly simple and
      easy to distinguish. In a free hour, when our power of choice is
      untrammelled and when nothing prevents our being able to do what we like
      best, every pleasure is to be welcomed and every pain avoided. But in
      certain circumstances and owing to the claims of duty or the obligations
      of business it will frequently occur that pleasures have to be repudiated
      and annoyances accepted. The wise man therefore always holds in these
      matters to this principle of selection: he rejects pleasures to secure
      other greater pleasures, or else he endures pains to avoid worse pains."
      help@lipsum.com Privacy Policy · Do Not Sell My Personal Information ·
      Change Consent
    </div>
  );
};

export default Lorem;
```

```javascript
import React from "react";

const Home = () => {
  return (
    <div>
      What is Lorem Ipsum? Lorem Ipsum is simply dummy text of the printing and
      typesetting industry. Lorem Ipsum has been the industry's standard dummy
      text ever since the 1500s, when an unknown printer took a galley of type
      and scrambled it to make a type specimen book. It has survived not only
      five centuries, but also the leap into electronic typesetting, remaining
      essentially unchanged. It was popularised in the 1960s with the release of
      Letraset sheets containing Lorem Ipsum passages, and more recently with
      desktop publishing software like Aldus PageMaker including versions of
      Lorem Ipsum. Why do we use it? It is a long established fact that a reader
      will be distracted by the readable content of a page when looking at its
      layout. The point of using Lorem Ipsum is that it has a more-or-less
      normal distribution of letters, as opposed to using 'Content here, content
      here', making it look like readable English. Many desktop publishing
      packages and web page editors now use Lorem Ipsum as their default model
      text, and a search for 'lorem ipsum' will uncover many web sites still in
      their infancy. Various versions have evolved over the years, sometimes by
      accident, sometimes on purpose (injected humour and the like). Where does
      it come from? Contrary to popular belief, Lorem Ipsum is not simply random
      text. It has roots in a piece of classical Latin literature from 45 BC,
      making it over 2000 years old. Richard McClintock, a Latin professor at
      Hampden-Sydney College in Virginia, looked up one of the more obscure
      Latin words, consectetur, from a Lorem Ipsum passage, and going through
      the cites of the word in classical literature, discovered the undoubtable
      source. Lorem Ipsum comes from sections 1.10.32 and 1.10.33 of "de Finibus
      Bonorum et Malorum" (The Extremes of Good and Evil) by Cicero, written in
      45 BC. This book is a treatise on the theory of ethics, very popular
      during the Renaissance. The first line of Lorem Ipsum, "Lorem ipsum dolor
      sit amet..", comes from a line in section 1.10.32. The standard chunk of
      Lorem Ipsum used since the 1500s is reproduced below for those interested.
      Sections 1.10.32 and 1.10.33 from "de Finibus Bonorum et Malorum" by
      Cicero are also reproduced in their exact original form, accompanied by
      English versions from the 1914 translation by H. Rackham. Where can I get
      some? There are many variations of passages of Lorem Ipsum available, but
      the majority have suffered alteration in some form, by injected humour, or
      randomised words which don't look even slightly believable. If you are
      going to use a passage of Lorem Ipsum, you need to be sure there isn't
      anything embarrassing hidden in the middle of text. All the Lorem Ipsum
      generators on the Internet tend to repeat predefined chunks as necessary,
      making this the first true generator on the Internet. It uses a dictionary
      of over 200 Latin words, combined with a handful of model sentence
      structures, to generate Lorem Ipsum which looks reasonable. The generated
      Lorem Ipsum is therefore always free from repetition, injected humour, or
      non-characteristic words etc. 5 paragraphs words bytes lists Start with
      'Lorem ipsum dolor sit amet...' Translations: Can you help translate this
      site into a foreign language ? Please email us with details if you can
      help. There is a set of mock banners available here in three colours and
      in a range of standard banner sizes: BannersBannersBanners Donate: If you
      use this site regularly and would like to help keep the site on the
      Internet, please consider donating a small sum to help pay for the hosting
      and bandwidth bill. There is no minimum donation, any sum is appreciated -
      click here to donate using PayPal. Thank you for your support. Donate
      Bitcoin: 16UQLq1HZ3CNwhvgrarV6pMoA2CDjb4tyF NodeJS Python Interface GTK
      Lipsum Rails .NET Groovy The standard Lorem Ipsum passage, used since the
      1500s "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do
      eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad
      minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex
      ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate
      velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat
      cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id
      est laborum." Section 1.10.32 of "de Finibus Bonorum et Malorum", written
      by Cicero in 45 BC "Sed ut perspiciatis unde omnis iste natus error sit
      voluptatem accusantium doloremque laudantium, totam rem aperiam, eaque
      ipsa quae ab illo inventore veritatis et quasi architecto beatae vitae
      dicta sunt explicabo. Nemo enim ipsam voluptatem quia voluptas sit
      aspernatur aut odit aut fugit, sed quia consequuntur magni dolores eos qui
      ratione voluptatem sequi nesciunt. Neque porro quisquam est, qui dolorem
      ipsum quia dolor sit amet, consectetur, adipisci velit, sed quia non
      numquam eius modi tempora incidunt ut labore et dolore magnam aliquam
      quaerat voluptatem. Ut enim ad minima veniam, quis nostrum exercitationem
      ullam corporis suscipit laboriosam, nisi ut aliquid ex ea commodi
      consequatur? Quis autem vel eum iure reprehenderit qui in ea voluptate
      velit esse quam nihil molestiae consequatur, vel illum qui dolorem eum
      fugiat quo voluptas nulla pariatur?" 1914 translation by H. Rackham "But I
      must explain to you how all this mistaken idea of denouncing pleasure and
      praising pain was born and I will give you a complete account of the
      system, and expound the actual teachings of the great explorer of the
      truth, the master-builder of human happiness. No one rejects, dislikes, or
      avoids pleasure itself, because it is pleasure, but because those who do
      not know how to pursue pleasure rationally encounter consequences that are
      extremely painful. Nor again is there anyone who loves or pursues or
      desires to obtain pain of itself, because it is pain, but because
      occasionally circumstances occur in which toil and pain can procure him
      some great pleasure. To take a trivial example, which of us ever
      undertakes laborious physical exercise, except to obtain some advantage
      from it? But who has any right to find fault with a man who chooses to
      enjoy a pleasure that has no annoying consequences, or one who avoids a
      pain that produces no resultant pleasure?" Section 1.10.33 of "de Finibus
      Bonorum et Malorum", written by Cicero in 45 BC "At vero eos et accusamus
      et iusto odio dignissimos ducimus qui blanditiis praesentium voluptatum
      deleniti atque corrupti quos dolores et quas molestias excepturi sint
      occaecati cupiditate non provident, similique sunt in culpa qui officia
      deserunt mollitia animi, id est laborum et dolorum fuga. Et harum quidem
      rerum facilis est et expedita distinctio. Nam libero tempore, cum soluta
      nobis est eligendi optio cumque nihil impedit quo minus id quod maxime
      placeat facere possimus, omnis voluptas assumenda est, omnis dolor
      repellendus. Temporibus autem quibusdam et aut officiis debitis aut rerum
      necessitatibus saepe eveniet ut et voluptates repudiandae sint et
      molestiae non recusandae. Itaque earum rerum hic tenetur a sapiente
      delectus, ut aut reiciendis voluptatibus maiores alias consequatur aut
      perferendis doloribus asperiores repellat." 1914 translation by H. Rackham
      "On the other hand, we denounce with righteous indignation and dislike men
      who are so beguiled and demoralized by the charms of pleasure of the
      moment, so blinded by desire, that they cannot foresee the pain and
      trouble that are bound to ensue; and equal blame belongs to those who fail
      in their duty through weakness of will, which is the same as saying
      through shrinking from toil and pain. These cases are perfectly simple and
      easy to distinguish. In a free hour, when our power of choice is
      untrammelled and when nothing prevents our being able to do what we like
      best, every pleasure is to be welcomed and every pain avoided. But in
      certain circumstances and owing to the claims of duty or the obligations
      of business it will frequently occur that pleasures have to be repudiated
      and annoyances accepted. The wise man therefore always holds in these
      matters to this principle of selection: he rejects pleasures to secure
      other greater pleasures, or else he endures pains to avoid worse pains."
      help@lipsum.com Privacy Policy · Do Not Sell My Personal Information ·
      Change Consent
      <div>
        What is Lorem Ipsum? Lorem Ipsum is simply dummy text of the printing
        and typesetting industry. Lorem Ipsum has been the industry's standard
        dummy text ever since the 1500s, when an unknown printer took a galley
        of type and scrambled it to make a type specimen book. It has survived
        not only five centuries, but also the leap into electronic typesetting,
        remaining essentially unchanged. It was popularised in the 1960s with
        the release of Letraset sheets containing Lorem Ipsum passages, and more
        recently with desktop publishing software like Aldus PageMaker including
        versions of Lorem Ipsum. Why do we use it? It is a long established fact
        that a reader will be distracted by the readable content of a page when
        looking at its layout. The point of using Lorem Ipsum is that it has a
        more-or-less normal distribution of letters, as opposed to using
        'Content here, content here', making it look like readable English. Many
        desktop publishing packages and web page editors now use Lorem Ipsum as
        their default model text, and a search for 'lorem ipsum' will uncover
        many web sites still in their infancy. Various versions have evolved
        over the years, sometimes by accident, sometimes on purpose (injected
        humour and the like). Where does it come from? Contrary to popular
        belief, Lorem Ipsum is not simply random text. It has roots in a piece
        of classical Latin literature from 45 BC, making it over 2000 years old.
        Richard McClintock, a Latin professor at Hampden-Sydney College in
        Virginia, looked up one of the more obscure Latin words, consectetur,
        from a Lorem Ipsum passage, and going through the cites of the word in
        classical literature, discovered the undoubtable source. Lorem Ipsum
        comes from sections 1.10.32 and 1.10.33 of "de Finibus Bonorum et
        Malorum" (The Extremes of Good and Evil) by Cicero, written in 45 BC.
        This book is a treatise on the theory of ethics, very popular during the
        Renaissance. The first line of Lorem Ipsum, "Lorem ipsum dolor sit
        amet..", comes from a line in section 1.10.32. The standard chunk of
        Lorem Ipsum used since the 1500s is reproduced below for those
        interested. Sections 1.10.32 and 1.10.33 from "de Finibus Bonorum et
        Malorum" by Cicero are also reproduced in their exact original form,
        accompanied by English versions from the 1914 translation by H. Rackham.
        Where can I get some? There are many variations of passages of Lorem
        Ipsum available, but the majority have suffered alteration in some form,
        by injected humour, or randomised words which don't look even slightly
        believable. If you are going to use a passage of Lorem Ipsum, you need
        to be sure there isn't anything embarrassing hidden in the middle of
        text. All the Lorem Ipsum generators on the Internet tend to repeat
        predefined chunks as necessary, making this the first true generator on
        the Internet. It uses a dictionary of over 200 Latin words, combined
        with a handful of model sentence structures, to generate Lorem Ipsum
        which looks reasonable. The generated Lorem Ipsum is therefore always
        free from repetition, injected humour, or non-characteristic words etc.
        5 paragraphs words bytes lists Start with 'Lorem ipsum dolor sit
        amet...' Translations: Can you help translate this site into a foreign
        language ? Please email us with details if you can help. There is a set
        of mock banners available here in three colours and in a range of
        standard banner sizes: BannersBannersBanners Donate: If you use this
        site regularly and would like to help keep the site on the Internet,
        please consider donating a small sum to help pay for the hosting and
        bandwidth bill. There is no minimum donation, any sum is appreciated -
        click here to donate using PayPal. Thank you for your support. Donate
        Bitcoin: 16UQLq1HZ3CNwhvgrarV6pMoA2CDjb4tyF NodeJS Python Interface GTK
        Lipsum Rails .NET Groovy The standard Lorem Ipsum passage, used since
        the 1500s "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed
        do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim
        ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut
        aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit
        in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
        Excepteur sint occaecat cupidatat non proident, sunt in culpa qui
        officia deserunt mollit anim id est laborum." Section 1.10.32 of "de
        Finibus Bonorum et Malorum", written by Cicero in 45 BC "Sed ut
        perspiciatis unde omnis iste natus error sit voluptatem accusantium
        doloremque laudantium, totam rem aperiam, eaque ipsa quae ab illo
        inventore veritatis et quasi architecto beatae vitae dicta sunt
        explicabo. Nemo enim ipsam voluptatem quia voluptas sit aspernatur aut
        odit aut fugit, sed quia consequuntur magni dolores eos qui ratione
        voluptatem sequi nesciunt. Neque porro quisquam est, qui dolorem ipsum
        quia dolor sit amet, consectetur, adipisci velit, sed quia non numquam
        eius modi tempora incidunt ut labore et dolore magnam aliquam quaerat
        voluptatem. Ut enim ad minima veniam, quis nostrum exercitationem ullam
        corporis suscipit laboriosam, nisi ut aliquid ex ea commodi consequatur?
        Quis autem vel eum iure reprehenderit qui in ea voluptate velit esse
        quam nihil molestiae consequatur, vel illum qui dolorem eum fugiat quo
        voluptas nulla pariatur?" 1914 translation by H. Rackham "But I must
        explain to you how all this mistaken idea of denouncing pleasure and
        praising pain was born and I will give you a complete account of the
        system, and expound the actual teachings of the great explorer of the
        truth, the master-builder of human happiness. No one rejects, dislikes,
        or avoids pleasure itself, because it is pleasure, but because those who
        do not know how to pursue pleasure rationally encounter consequences
        that are extremely painful. Nor again is there anyone who loves or
        pursues or desires to obtain pain of itself, because it is pain, but
        because occasionally circumstances occur in which toil and pain can
        procure him some great pleasure. To take a trivial example, which of us
        ever undertakes laborious physical exercise, except to obtain some
        advantage from it? But who has any right to find fault with a man who
        chooses to enjoy a pleasure that has no annoying consequences, or one
        who avoids a pain that produces no resultant pleasure?" Section 1.10.33
        of "de Finibus Bonorum et Malorum", written by Cicero in 45 BC "At vero
        eos et accusamus et iusto odio dignissimos ducimus qui blanditiis
        praesentium voluptatum deleniti atque corrupti quos dolores et quas
        molestias excepturi sint occaecati cupiditate non provident, similique
        sunt in culpa qui officia deserunt mollitia animi, id est laborum et
        dolorum fuga. Et harum quidem rerum facilis est et expedita distinctio.
        Nam libero tempore, cum soluta nobis est eligendi optio cumque nihil
        impedit quo minus id quod maxime placeat facere possimus, omnis voluptas
        assumenda est, omnis dolor repellendus. Temporibus autem quibusdam et
        aut officiis debitis aut rerum necessitatibus saepe eveniet ut et
        voluptates repudiandae sint et molestiae non recusandae. Itaque earum
        rerum hic tenetur a sapiente delectus, ut aut reiciendis voluptatibus
        maiores alias consequatur aut perferendis doloribus asperiores
        repellat." 1914 translation by H. Rackham "On the other hand, we
        denounce with righteous indignation and dislike men who are so beguiled
        and demoralized by the charms of pleasure of the moment, so blinded by
        desire, that they cannot foresee the pain and trouble that are bound to
        ensue; and equal blame belongs to those who fail in their duty through
        weakness of will, which is the same as saying through shrinking from
        toil and pain. These cases are perfectly simple and easy to distinguish.
        In a free hour, when our power of choice is untrammelled and when
        nothing prevents our being able to do what we like best, every pleasure
        is to be welcomed and every pain avoided. But in certain circumstances
        and owing to the claims of duty or the obligations of business it will
        frequently occur that pleasures have to be repudiated and annoyances
        accepted. The wise man therefore always holds in these matters to this
        principle of selection: he rejects pleasures to secure other greater
        pleasures, or else he endures pains to avoid worse pains."
        help@lipsum.com Privacy Policy · Do Not Sell My Personal Information ·
        Change Consent
      </div>
      <div>
        What is Lorem Ipsum? Lorem Ipsum is simply dummy text of the printing
        and typesetting industry. Lorem Ipsum has been the industry's standard
        dummy text ever since the 1500s, when an unknown printer took a galley
        of type and scrambled it to make a type specimen book. It has survived
        not only five centuries, but also the leap into electronic typesetting,
        remaining essentially unchanged. It was popularised in the 1960s with
        the release of Letraset sheets containing Lorem Ipsum passages, and more
        recently with desktop publishing software like Aldus PageMaker including
        versions of Lorem Ipsum. Why do we use it? It is a long established fact
        that a reader will be distracted by the readable content of a page when
        looking at its layout. The point of using Lorem Ipsum is that it has a
        more-or-less normal distribution of letters, as opposed to using
        'Content here, content here', making it look like readable English. Many
        desktop publishing packages and web page editors now use Lorem Ipsum as
        their default model text, and a search for 'lorem ipsum' will uncover
        many web sites still in their infancy. Various versions have evolved
        over the years, sometimes by accident, sometimes on purpose (injected
        humour and the like). Where does it come from? Contrary to popular
        belief, Lorem Ipsum is not simply random text. It has roots in a piece
        of classical Latin literature from 45 BC, making it over 2000 years old.
        Richard McClintock, a Latin professor at Hampden-Sydney College in
        Virginia, looked up one of the more obscure Latin words, consectetur,
        from a Lorem Ipsum passage, and going through the cites of the word in
        classical literature, discovered the undoubtable source. Lorem Ipsum
        comes from sections 1.10.32 and 1.10.33 of "de Finibus Bonorum et
        Malorum" (The Extremes of Good and Evil) by Cicero, written in 45 BC.
        This book is a treatise on the theory of ethics, very popular during the
        Renaissance. The first line of Lorem Ipsum, "Lorem ipsum dolor sit
        amet..", comes from a line in section 1.10.32. The standard chunk of
        Lorem Ipsum used since the 1500s is reproduced below for those
        interested. Sections 1.10.32 and 1.10.33 from "de Finibus Bonorum et
        Malorum" by Cicero are also reproduced in their exact original form,
        accompanied by English versions from the 1914 translation by H. Rackham.
        Where can I get some? There are many variations of passages of Lorem
        Ipsum available, but the majority have suffered alteration in some form,
        by injected humour, or randomised words which don't look even slightly
        believable. If you are going to use a passage of Lorem Ipsum, you need
        to be sure there isn't anything embarrassing hidden in the middle of
        text. All the Lorem Ipsum generators on the Internet tend to repeat
        predefined chunks as necessary, making this the first true generator on
        the Internet. It uses a dictionary of over 200 Latin words, combined
        with a handful of model sentence structures, to generate Lorem Ipsum
        which looks reasonable. The generated Lorem Ipsum is therefore always
        free from repetition, injected humour, or non-characteristic words etc.
        5 paragraphs words bytes lists Start with 'Lorem ipsum dolor sit
        amet...' Translations: Can you help translate this site into a foreign
        language ? Please email us with details if you can help. There is a set
        of mock banners available here in three colours and in a range of
        standard banner sizes: BannersBannersBanners Donate: If you use this
        site regularly and would like to help keep the site on the Internet,
        please consider donating a small sum to help pay for the hosting and
        bandwidth bill. There is no minimum donation, any sum is appreciated -
        click here to donate using PayPal. Thank you for your support. Donate
        Bitcoin: 16UQLq1HZ3CNwhvgrarV6pMoA2CDjb4tyF NodeJS Python Interface GTK
        Lipsum Rails .NET Groovy The standard Lorem Ipsum passage, used since
        the 1500s "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed
        do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim
        ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut
        aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit
        in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
        Excepteur sint occaecat cupidatat non proident, sunt in culpa qui
        officia deserunt mollit anim id est laborum." Section 1.10.32 of "de
        Finibus Bonorum et Malorum", written by Cicero in 45 BC "Sed ut
        perspiciatis unde omnis iste natus error sit voluptatem accusantium
        doloremque laudantium, totam rem aperiam, eaque ipsa quae ab illo
        inventore veritatis et quasi architecto beatae vitae dicta sunt
        explicabo. Nemo enim ipsam voluptatem quia voluptas sit aspernatur aut
        odit aut fugit, sed quia consequuntur magni dolores eos qui ratione
        voluptatem sequi nesciunt. Neque porro quisquam est, qui dolorem ipsum
        quia dolor sit amet, consectetur, adipisci velit, sed quia non numquam
        eius modi tempora incidunt ut labore et dolore magnam aliquam quaerat
        voluptatem. Ut enim ad minima veniam, quis nostrum exercitationem ullam
        corporis suscipit laboriosam, nisi ut aliquid ex ea commodi consequatur?
        Quis autem vel eum iure reprehenderit qui in ea voluptate velit esse
        quam nihil molestiae consequatur, vel illum qui dolorem eum fugiat quo
        voluptas nulla pariatur?" 1914 translation by H. Rackham "But I must
        explain to you how all this mistaken idea of denouncing pleasure and
        praising pain was born and I will give you a complete account of the
        system, and expound the actual teachings of the great explorer of the
        truth, the master-builder of human happiness. No one rejects, dislikes,
        or avoids pleasure itself, because it is pleasure, but because those who
        do not know how to pursue pleasure rationally encounter consequences
        that are extremely painful. Nor again is there anyone who loves or
        pursues or desires to obtain pain of itself, because it is pain, but
        because occasionally circumstances occur in which toil and pain can
        procure him some great pleasure. To take a trivial example, which of us
        ever undertakes laborious physical exercise, except to obtain some
        advantage from it? But who has any right to find fault with a man who
        chooses to enjoy a pleasure that has no annoying consequences, or one
        who avoids a pain that produces no resultant pleasure?" Section 1.10.33
        of "de Finibus Bonorum et Malorum", written by Cicero in 45 BC "At vero
        eos et accusamus et iusto odio dignissimos ducimus qui blanditiis
        praesentium voluptatum deleniti atque corrupti quos dolores et quas
        molestias excepturi sint occaecati cupiditate non provident, similique
        sunt in culpa qui officia deserunt mollitia animi, id est laborum et
        dolorum fuga. Et harum quidem rerum facilis est et expedita distinctio.
        Nam libero tempore, cum soluta nobis est eligendi optio cumque nihil
        impedit quo minus id quod maxime placeat facere possimus, omnis voluptas
        assumenda est, omnis dolor repellendus. Temporibus autem quibusdam et
        aut officiis debitis aut rerum necessitatibus saepe eveniet ut et
        voluptates repudiandae sint et molestiae non recusandae. Itaque earum
        rerum hic tenetur a sapiente delectus, ut aut reiciendis voluptatibus
        maiores alias consequatur aut perferendis doloribus asperiores
        repellat." 1914 translation by H. Rackham "On the other hand, we
        denounce with righteous indignation and dislike men who are so beguiled
        and demoralized by the charms of pleasure of the moment, so blinded by
        desire, that they cannot foresee the pain and trouble that are bound to
        ensue; and equal blame belongs to those who fail in their duty through
        weakness of will, which is the same as saying through shrinking from
        toil and pain. These cases are perfectly simple and easy to distinguish.
        In a free hour, when our power of choice is untrammelled and when
        nothing prevents our being able to do what we like best, every pleasure
        is to be welcomed and every pain avoided. But in certain circumstances
        and owing to the claims of duty or the obligations of business it will
        frequently occur that pleasures have to be repudiated and annoyances
        accepted. The wise man therefore always holds in these matters to this
        principle of selection: he rejects pleasures to secure other greater
        pleasures, or else he endures pains to avoid worse pains."
        help@lipsum.com Privacy Policy · Do Not Sell My Personal Information ·
        Change Consent
      </div>
    </div>
  );
};

export default Home;
```

<br/>
<hr/>
<br/>

### Chapter 20: Helper

```javascript
// App
import React, { useEffect } from "react";
import { TwentygetAllUsers } from "./TwentygetAllUsers";
import { addNum } from "./addTwo";

const TwentyApp = () => {
  /* const getUsers = ()=>{
		fetch("https://jsonplaceholder.typicode.com/users")
		.then(response=> response.json())
		.then(json => console.log(json))
	} */

  const getUsersHelper = async () => {
    let data = await TwentygetAllUsers();
    console.log(data);
  };

  const addTwoNumsHelper = async () => {
    let twoAdd = await addNum(2, 3);
    console.log(twoAdd);
  };

  useEffect(() => {
    getUsersHelper();
    addTwoNumsHelper();
  }, []);

  return (
    <div>
      <h1>Helper function</h1>
    </div>
  );
};

export default TwentyApp;
```

```javascript
export const TwentygetAllUsers = () => {
  return fetch("https://jsonplaceholder.typicode.com/users")
    .then((response) => response.json())
    .then((json) => console.log(json));
};
```

```javascript
export const addNum = (a, b) => {
  return a + b;
};
```

<br/>
<hr/>
<br/>

### Chapter 21: NA

```javascript
```

<br/>
<hr/>
<br/>

### Chapter 22: Recursion

```javascript
// App
import Family from "./Family";
import { familyTree } from "./data";

const RecursionApp = () => {
  return (
    <div>
      <Family familyTree={familyTree} /> {/* Step 1*/}
    </div>
  );
};

export default RecursionApp;
```

```javascript
import React, { useState } from "react";

{
  /* Step 2*/
}
const Family = ({ familyTree }) => {
  const [isVisible, setIsVisible] = useState(false);

  const expand = () => {
    setIsVisible(!isVisible);
  };

  return (
    <div style={{ paddingLeft: 10 }}>
      <span onClick={expand}>{familyTree.name}</span>

      {isVisible ? (
        familyTree?.children?.map((child) => {
          return (
            <div style={{ paddingLeft: 10 }}>
              {/* <span>{child.name}</span> */}
              <Family familyTree={child} />
              {/* Step 4: This is recursion*/}
            </div>
          );
        })
      ) : (
        <></>
      )}
    </div>
  );
};

export default Family;
```

```javascript
{
  /* Step 3*/
}
export const familyTree = {
  name: "John",
  age: 90,
  children: [
    {
      name: "Mary",
      age: 60
    },
    {
      name: "Arthur",
      age: 60,
      children: [
        {
          name: "Lily",
          age: 35,
          children: [
            {
              name: "Hank",
              age: 60
            },
            {
              name: "Henry",
              age: 57
            }
          ]
        },
        {
          name: "Billy",
          age: 37
        }
      ]
    },
    {
      name: "Dolores",
      age: 55
    }
  ]
};
```

<br/>
<hr/>
<br/>

### Chapter 23: Array

```javascript
import React, { useEffect } from "react";

const TwentyThreeArray = () => {
  //Example 2: Array of object
  const fnArray = [
    {
      fn: function add(a, b) {
        return a + b;
      }
    },
    {
      fn: function sub(a, b) {
        return a - b;
      }
    },
    {
      fn: function mult(a, b) {
        return a * b;
      }
    },
    {
      fn: function div(a, b) {
        return a / b;
      }
    }
  ];

  //Example 1: Array of function
  /* const fnArray = [
		function fnAdd(a,b){
			return a + b
		},
		function fnSub(a,b){
			return a - b
		},
		function fnMult(a,b){
			return a*b
		},
		function fnDiv(a,b){
			return a / b;
		}
	] */

  const mainFn = () => {
    //Example 2: To call array of object
    let result = fnArray.map((item) => {
      return item.fn(4, 2);
    });

    //Example 1: To call array of function
    /* let result = fnArray.map(fn=>{
			return fn(4,2);
		}) */
    console.log(result);
  };

  useEffect(() => {
    mainFn();
  }, []);

  return (
    <div className="App">
      <h3>
        Write a function which takes an array of multiple functions and execute
        them one by one in left to right manner.
      </h3>

      <h3>- By Zomato</h3>
    </div>
  );
};

export default TwentyThreeArray;
```

<br/>
<hr/>
<br/>

### Chapter 24: Custom Hooks

```javascript
import React, { useEffect, useState } from "react";

import useData from "./useJSONPlaceholder";

const TwentyFourCustomHookApp = () => {
  let { users, posts } = useData();

  return (
    <div>
      <h1>Users</h1>
      {users.slice(0, 10).map((user) => {
        return <h3>{user.name}</h3>;
      })}
      <h1>Posts</h1>
      {posts.slice(0, 10).map((post) => {
        return <h3>{post.title}</h3>;
      })}
    </div>
  );
};

export default TwentyFourCustomHookApp;
```

```javascript
import { useEffect, useState } from "react";

const useData = () => {
  const [users, setUsers] = useState([]);
  const [posts, setPosts] = useState([]);

  const getUsers = () => {
    fetch(`https://jsonplaceholder.typicode.com/users`)
      .then((response) => response.json())
      .then((json) => setUsers(json));
  };

  const getPosts = () => {
    fetch(`https://jsonplaceholder.typicode.com/posts`)
      .then((response) => response.json())
      .then((json) => setPosts(json));
  };

  useEffect(() => {
    getUsers();
    getPosts();
  }, []);

  return { users, posts };
};

export default useData;
```

<br/>
<hr/>
<br/>

### Chapter 25: Promise, Aysnc-await

```javascript
import React, { useEffect } from "react";

/*Notes:
- I promise my friend that I will give him a chocoloate everyday, 
	if i fail to give him then I break the promise.
- If the promise is completed, it is resolved otherwise it is rejected.
*/
const PromiseApp = () => {
  const promiseExample = () => {
    // Promise creation
    const friend = new Promise((resolve, reject) => {
      let isChocoloteEveryday = true;

      if (isChocoloteEveryday) {
        resolve("Promise resolved");
      } else {
        reject("Promise Broken");
      }
    });

    // Promise call
    friend
      .then((response) => console.log(`${response}`))
      .catch((error) => console.log(`${error} No more friendship`));
  };

  useEffect(() => {
    promiseExample();
  }, []);

  return <div>PromiseApp</div>;
};

export default PromiseApp;
```

```javascript
import React, { useEffect } from "react";

const PromiseApp2 = () => {
  // Step 1: Promise creation
  const promiseOne = (paramOne) => {
    return new Promise((resolve, reject) => {
      if (paramOne === "Sarfaraz") {
        resolve("Promise Resolved");
      } else {
        reject("Promise Rejected");
      }
    });
  };

  // Step 1: Promise creation
  const promiseTwo = (paramTwo) => {
    return new Promise((resolve, reject) => {
      if (paramTwo === "Promise Resolved") {
        resolve("Sarfaraz is good programmer");
      } else {
        reject("Sarfaraz is still a good programmer");
      }
    });
  };

  // Step 2: Promise call, call method with some parameters
  const promiseMain = () => {
    promiseOne("Sarfaraz")
      .then((firstResponse) => {
        console.log(firstResponse);
        return promiseTwo(firstResponse);
      })
      .then((secondResponse) => console.log(secondResponse))
      .catch((error) => console.log(error));
  };

  // Step 2: Promise call, call method with some parameters
  //Async Await syntax : prefered to use due to shorter syntax
  const asyncMain = async () => {
    try {
      let firstResponse = await promiseOne("Sarfaraz");
      let secondResponse = await promiseTwo(firstResponse);
      console.log(firstResponse);
      console.log(secondResponse);
    } catch (error) {
      console.log(`Promise rejected`);
    }
  };

  // Step 3:
  useEffect(() => {
    promiseMain();
    asyncMain();
  }, []);

  return <div>PromiseApp2</div>;
};

export default PromiseApp2;
```

<br/>
<hr/>
<br/>

### Chapter 26: Code Spliting

```javascript
import React, { useEffect } from "react";
// import { add } from './Math'; //Approach1: step 1

/*Notes:
-	Code splitting will create multiple bundles, as when project size increase then bundle also increases, 
to avoid this, we use this code spliiting.
-	Code spliting will be loaded at run time.

*/
const CodesplitingApp = () => {
  useEffect(() => {
    add();
  }, []);

  const add = () => {
    //Approach1: step 2
    // let sum = add(5,6);
    // console.log(sum);

    //Approach2: step 1 Only: This is Dynamic Import, which improve the performance
    import("./Math").then((math) => {
      let sum = math.add(2, 2);
      console.log(sum);
    });
  };
  return (
    <div>
      <button onClick={add}>Add</button>
    </div>
  );
};

export default CodesplitingApp;
```

```javascript
import React from "react";

export function add(a, b) {
  return a + b;
}
```

<br/>
<hr/>
<br/>

### Chapter 27: Filter

```javascript
import React, { useEffect, useState } from "react";

const FilterApp = () => {
  const [users, setUsers] = useState([]); //state for display the data
  const [searchQuery, setSearch] = useState([]); //state for earch record
  const [searched, setSearched] = useState([]); //state for display searched record

  const url = `https://jsonplaceholder.typicode.com/users`;

  const getData = () => {
    fetch(`https://jsonplaceholder.typicode.com/users`)
      .then((response) => response.json())
      .then((json) => setUsers(json));
  };

  useEffect(() => {
    getData();
  }, []);

  //filter logic: convert object into array then join then --> convert string into lowercase
  useEffect(() => {
    if (searchQuery) {
      // Creating search with debounce
      const searched = setTimeout(() => {
        setSearched(
          users.filter((user) => {
            return Object.values(user)
              .join("")
              .toLowerCase()
              .includes(searchQuery.toLowerCase());
          })
        );
      }, 1000);
      return () => clearTimeout(searched);
    } else {
      setUsers(users);
    }
  }, [searchQuery]);

  return (
    <div className="App">
      <input
        placeholder="Search input"
        className="search"
        onChange={(event) => setSearch(event.target.value)}
      />
      <div className="grid-main">
        {searchQuery.length > 0
          ? searched.map((search) => {
              return (
                <div className="grid-child">
                  <h4>{search.name}</h4>
                  <p>{search.username}</p>
                </div>
              );
            })
          : users.map((user) => {
              return (
                <div className="grid-child">
                  <h4>{user.name}</h4>
                  <p>{user.username}</p>
                </div>
              );
            })}
      </div>
    </div>
  );
};

export default FilterApp;
```

<br/>
<hr/>
<br/>

### Chapter 28: NA

```javascript
```

<br/>
<hr/>
<br/>

### Chapter 29: Unit Testing

```javascript
import React, { useState } from "react";

const Counter = () => {
  const [count, setCount] = useState(0);

  return (
    <div className="App">
      <h1 data-testid="countid">{count}</h1>
      <button onClick={() => setCount(count + 1)}>Increment Count</button>
    </div>
  );
};

export default Counter;
```

```javascript
import React from "react";
import { fireEvent, render } from "@testing-library/react";
import Counter from "./Counter";

/* test('Check the initial value of count',()=>{
	const {getByTestId} = render(<Counter inititailValue={0}/>)
	let counter = parseInt(getByTestId("countId").textContent);

	expect(counter).toEqual(0)
}) */

test("Check the initial value of count", () => {
  const { getByTestId } = render(<Counter initialValue={0} />);
  let counter = parseInt(getByTestId("countid").textContent);

  expect(Number(counter)).toEqual(0);
});

test("Check the increment button", () => {
  const { getByTestId, getByRole } = render(<Counter initialValue={0} />);
  let counter = parseInt(getByTestId("countid").textContent);
  expect(Number(counter)).toEqual(0);

  let incrementBtn = getByRole("button", { name: "Increment Count" });
  fireEvent.click(incrementBtn);

  let counterInc = getByTestId("countid").textContent;
  expect(Number(counterInc)).toEqual(1);
});
```

<br/>
<hr/>
<br/>

### Chapter 30: React Query

```javascript
// App
import React from "react";
import { BrowserRouter as Router, Routes, Route } from "react-router-dom";
import NormalCall from "./NormalCall";
import CachedCall from "./CachedCall";
import { QueryClient, QueryClientProvider } from "react-query";

const ReactQueryApp = () => {
  //create the instance
  let queryClient = new QueryClient();

  return (
    <QueryClientProvider client={queryClient}>
      <Router>
        <div>
          <Routes>
            <Route path="/normal-call" element={<NormalCall />} />
            <Route path="/cached-call" element={<CachedCall />} />
          </Routes>
        </div>
      </Router>
    </QueryClientProvider>
  );
};

export default ReactQueryApp;
```

```javascript
import React, { useEffect, useState } from "react";

const NormalCall = () => {
  const [data, setData] = useState([]);
  const [loading, setLoading] = useState(true);

  useEffect(() => {
    fetch(`https://jsonplaceholder.typicode.com/albums`)
      .then((response) => response.json())
      .then((json) => {
        setData(json);
        setLoading(false);
      });
  }, []);

  if (loading) return <h1>Loading...</h1>;
  return (
    <div>
      {data?.map((item) => {
        return (
          <h2>
            {item?.id}. {item?.title}
          </h2>
        );
      })}
    </div>
  );
};

export default NormalCall;
```

```javascript
import React from "react";
import { useQuery } from "react-query";
import { useNavigate } from "react-router-dom";

const CachedCall = () => {
  const { data, loading } = useQuery("data", () => {
    return fetch(
      "https://jsonplaceholder.typicode.com/albums"
    ).then((response) => response.json());
  });

  let navigate = useNavigate();
  if (loading) return <h1>Loading...</h1>;
  return (
    <div>
      <ul className="navbar">
        <li onClick={() => navigate("/normal-call")}>Normal Call</li>
        <li onClick={() => navigate("/cached-call")}>Cached Call</li>
      </ul>
      <h1>Cached call</h1>
      <div>
        {data?.map((item) => {
          return (
            <p>
              {item?.id}. {item?.title}
            </p>
          );
        })}
      </div>
    </div>
  );
};

export default CachedCall;
```

<br/>
<hr/>
<br/>

### Chapter 31: Pagination

```javascript
// App
import React, { useEffect, useState } from "react";
import Posts from "./Posts";
import PaginationComponent from "./PaginationComponent";

const PaginationApp = () => {
  const [posts, setPosts] = useState([]);
  let limit = 10;
  const [currentPage, setCurrentPage] = useState(1);

  useEffect(() => {
    fetch("https://jsonplaceholder.typicode.com/posts")
      .then((response) => response.json())
      .then((json) => setPosts(json));
  }, []);

  let lastIndex = currentPage * limit;
  let firstIndex = lastIndex - limit;

  // let currentItems = posts.slice(firstIndex, lastIndex);
  let currentItems = posts.slice(firstIndex, lastIndex);
  console.log("Current items:", currentItems);

  return (
    <div className="App">
      <Posts posts={posts} />
      <PaginationComponent
        currentPage={currentPage}
        limit={limit}
        totalPosts={posts?.length}
        setCurrentPage={setCurrentPage}
      />
    </div>
  );
};

export default PaginationApp;
```

```javascript
import React from "react";
import Pagination from "react-js-pagination";

const PaginationComponent = ({
  currentPage,
  limit,
  totalPosts,
  setCurrentPage
}) => {
  const handlePageChange = (pageNumber) => {
    console.log("Page changed to:", pageNumber);
    setCurrentPage(pageNumber);
  };

  let pages = totalPosts / limit;
  console.log("Total pages:", pages);

  return (
    <div>
      <Pagination
        activePage={currentPage}
        totalItemsCount={totalPosts}
        pageRangeDisplayed={5}
        onChange={(pageNumber) => handlePageChange(pageNumber)}
        activeClass="pagination-active"
        innerClass="pagination-button pagination"
      />
    </div>
  );
};

export default PaginationComponent;
```

```javascript
import React from "react";

const Posts = ({ posts }) => {
  return (
    <div>
      <h1>Posts</h1>
      <ul className="list-unstyled">
        {posts.map((post, index) => {
          return (
            <li style={{ padding: "10px" }}>
              {index + 1}. {post.title}
            </li>
          );
        })}
      </ul>
    </div>
  );
};

export default Posts;
```

```style
.pagination-button ul {
  list-style: none;
  display: flex;
}

.pagination-button > li {
  margin: 10px;
}

```

<br/>
<hr/>
<br/>

### Chapter 32: Infinite Scroll

```javascript
import React, { useState, useEffect, useRef, useCallback } from "react";
import axios from "axios";

const InfinitescrollApp = () => {
  const [search, setSearch] = useState("");
  const [posts, setPosts] = useState([]);
  const [pageNumber, setPageNumber] = useState(1);
  const [loading, setLoading] = useState(false);
  const observer = useRef();

  const handleSearch = (e) => {
    setSearch(e.target.value);
    setLoading(true);
    setPageNumber(1);
  };

  useEffect(() => {
    // setLoading(true);

    const debouncing = setTimeout(() => {
      axios
        .get(
          `http://openlibrary.org/search.json?q=${search.toLowerCase()}&page=${pageNumber}`
        )
        .then((res) => {
          setPosts((prev) => {
            //return the merged array
            return [...prev, ...res.data.docs.map((val) => val.title)];
          });
          setLoading(false);
        });
    }, 200);

    return () => {
      clearTimeout(debouncing);
    };
  }, [search, pageNumber]);

  let endofThePage = useCallback(
    (val) => {
      if (loading) return;

      if (observer.current) {
        observer.current.disconnect();
      }

      observer.current = new IntersectionObserver((item) => {
        //check if the item exists
        if (item[0].isIntersecting) {
          setPageNumber((prev) => prev + 1);
        }
      });

      //if there is value, then observe it
      if (val) observer.current.observe(val);
    },
    [loading]
  );

  return (
    <div className="App">
      <input
        type="text"
        placeholder="search"
        value={search}
        onChange={handleSearch}
      />

      {loading ? (
        <h1>Loading...</h1>
      ) : (
        <ul>
          {posts.map((book, index) => {
            if (posts.length === index + 1) {
              return <li ref={endofThePage}>{book}</li>;
            } else {
              return <li>{book}</li>;
            }
          })}
        </ul>
      )}
    </div>
  );
};

export default InfinitescrollApp;
```


