// new keyword

// the new keyword creates a brand new plain empty objects

class Product {
	// name;
	// price;
	// description;

	 constructor(n, p, d) {
        this.name = n;
        this.price = p;
        this.description = d;
		 		// constructor returns object
        // return "10"; // primitive -> no effect
        // return {x: 10};
        //return this; // if you dont return anything, it is equal to saying return this;
		 		// A class may have one constructor so constructor overloading is not allowed
    }

	display(){
		
	}
	
}

const p = new Product(); 
                  |
									|
									->   // this line calls the constructor of the class


// Constructor
// whenever we create object then constructor is the first function that is called
// constructor is a special method, if you dont call it javascript called by deafult constructor



const p = new Product("Bag", 100, "a cool bag");
console.log(p);











// function constructor
// we are not return anything in this function constructor because it return by deafult return this
function Product(n, p, d) {
    name = n;
    this.price = p;
    this.description = d;

    this.display = function () {
        console.log(name, this.price);
    }
}
const p = new Product("bag", 100, "cool new bag");
p.display();

// if we are not using new keyword then it behaves like normal function and this keyword here poits to widow object and it retun undefined in the absence of return keyword  








//  Prototyp in JS

// traditional oops -----> C++, Java

// class ----based on this blue print ----> object created



// but in the JS object is not based on the class blueprint, they are linked with blue print

// Waht happens when we run a js code

// before executing the first line of code, 

// Javascript maintain a function which caleed JS capital (O)Object, which provide a lot function like keys and value

// Apart from this there is an another object which has not any specific name but we can refer this object via property on this capital (O)Object function which is called prototype, in this object, toString(), valueOf() are occured which can't be defined for our own object like capital(O) Object

//Object.prototype

// and there is reverse chaining from this object to capital(O) Object, which is called constructor




// __proto__ (this prototype is called dunder proto)

// by using programetically (__proto__), we can acess the prototype

 // it is the property of Object.Prototype and dynamically reslove




//Inheritance

// Object.setPrototyprof

// it has multilevel inheritance not multiple inheritance






