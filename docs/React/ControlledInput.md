# Controlled Input

The standard method for dealing with input fields is to use a 'controlled input.' A controlled input is one in which the *onChange* event grabs the input, stores it to state then rerenders the component with the new value. Probably better with an example.

### Uncontrolled Input

This is not recommended in React.

````javascript
Class SearchBar extends React.Component {
    onInputChange(e) {
        console.log(e.target.value);
    }
    
    render() {
        return (
          <div>
            <form>
              <div>
                <label>Image Search</label>
                <input type="text" onChange={this.onInputChange} />
              </div>
            </form>
          </div>
        );
    }
}
````



### Controlled Input

The recommended method:

````javascript
Class SearchBar extends React.Component {
    constructor(props) {
      super(props);
      this.state = {term: '' };
    }
    render() {
        return (
          <div>
            <form>
              <div>
                <label>Image Search</label>
                <input
                  type="text"
                  value={this.state.term}
                  onChange={
                    e => this.setState({ term: e.target.value })
                  }
                />
              </div>
            </form>
          </div>
        );
    }
}
````

You could obviously still have the *onChange* call a separately defined method if needed.

````javascript
...
onInputChange = (e) => {     // use an arrow function or bind 'this' in the constructor
        console.log(e.target.value);
    }
...
                <input
                  type="text"
                  value={this.state.term}
                  onChange={this.onInputChange}
                />
...
````

With *bind* in the constructor

````javascript
constructor(props) {
    super(props);
    this.onInputChange = this.onInputChange.bind(this);
}
 onInputChange(e) {
        console.log(e.target.value);
    }
...
                <input
                  type="text"
                  value={this.state.term}
                  onChange={this.onInputChange}
                />
...
````

With an arrow function in the call

````javascript
onInputChange(e) {
        console.log(e.target.value);
    }
...
                <input
                  type="text"
                  value={this.state.term}
                  onChange={(e) => this.onInputChange(e)}
                />
...
````

You can bind in line also but not considered a best practice

````javascript
...
onInputChange(e) {
        console.log(e.target.value);
    }
...
                <input
                  type="text"
                  value={this.state.term}
                  onChange={this.onInputChange.bind(this)}
                />
...
````

