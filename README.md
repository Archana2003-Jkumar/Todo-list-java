# Todo-list-java
## Aim:
To code a to-do list using React.
## Code:
```
App.js
```
```
// App.js File
import React, { Component } from "react";
//import "bootstrap/dist/css/bootstrap.css";
import Container from "react-bootstrap/Container";
import Row from "react-bootstrap/Row";
import Col from "react-bootstrap/Col";
import Button from "react-bootstrap/Button";
import InputGroup from "react-bootstrap/InputGroup";
import FormControl from "react-bootstrap/FormControl";
import ListGroup from "react-bootstrap/ListGroup";

class App extends Component {
	constructor(props) {
		super(props);

		// Setting up state
		this.state = {
			userInput: "",
			list: [],
		};
	}

	// Set a user input value
	updateInput(value) {
		this.setState({
			userInput: value,
		});
	}

	// Add item if user input in not empty
	addItem() {
		if (this.state.userInput !== "") {
			const userInput = {
				// Add a random id which is used to delete
				id: Math.random(),

				// Add a user value to list
				value: this.state.userInput,
			};

			// Update list
			const list = [...this.state.list];
			list.push(userInput);

			// reset state
			this.setState({
				list,
				userInput: "",
			});
		}
	}

	// Function to delete item from list use id to delete
	deleteItem(key) {
		const list = [...this.state.list];

		// Filter values and leave value which we need to delete
		const updateList = list.filter((item) => item.id !== key);

		// Update list in state
		this.setState({
			list: updateList,
		});
	}

	render() {
		return (
			<Container>
      <Row className="color1" style={{display: "flex",justifyContent: "center",alignItems: "center",fontSize: "3rem",fontWeight: "bolder" }}  >
			TODO LIST
			</Row>

				<hr />
       
				<Row    className="box"> 
					<Col md={{ span: 5, offset: 4 }}>
						<InputGroup className="mb-3">
            
							<FormControl 
								placeholder="add item . . . "
								size="lg"
								value={this.state.userInput}
								onChange={(item) =>
									this.updateInput(item.target.value)
								}
								aria-label="add something"
								aria-describedby="basic-addon2"
							/>
							<InputGroup>
								<Button
									variant="dark"
									className="mt-2"
									onClick={() => this.addItem()}
								>
									ADD
								</Button>
							</InputGroup>
						</InputGroup>
					</Col>
				</Row>
				<Row   className="box2">
					<Col md={{ span: 5, offset: 4 }}>
						<ListGroup>
							{/* map over and print items */}
							{this.state.list.map((item) => {
								return (
									<ListGroup.Item
										variant="dark"
										action
										onClick={() => this.deleteItem(item.id)}
									>
										{item.value}
									</ListGroup.Item>
								);
							})}
						</ListGroup>
					</Col>
				</Row>
			</Container>
      
    );
	}
}

export default App;

```
```
indess.css
```
```
body {
  margin: 0;
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', 'Roboto', 'Oxygen',
    'Ubuntu', 'Cantarell', 'Fira Sans', 'Droid Sans', 'Helvetica Neue',
    sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

code {
  font-family: source-code-pro, Menlo, Monaco, Consolas, 'Courier New',
    monospace;
}
.color1{
  color: chartreuse;
}
.box{
height: 70px;
width: 500px;
background-color: rgb(118, 113, 113);
text-align: center;
margin-left: 435px;
font-size: 80px;

}
.box2{
  height: 200px;
  width: 500px;
  background-color: rgb(118, 113, 113);
  text-align: center;
  margin-left: 435px;
  font-size: 80px;
 
  }
```
## Output:
![image](https://github.com/Archana2003-Jkumar/Todo-list-java/assets/93427594/a837bdb6-a404-4212-b981-28a14e96baea)
## Result:
Hence the program has been successfully completed.
