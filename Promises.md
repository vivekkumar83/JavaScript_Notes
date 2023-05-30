code readbilty enchnaced
solve the problem of IOC

promises are special type of object that get return immediately when we call them

promises act as a placeholder for the data we hope to get back some where in the future

in these promises objects we can attach the functionality we want to execute once the future task is done

once the future task is done promises will automatically execute the attached functionallity

Promises:
1) how we can create a promise
2) how can we consume a promise


how we can create a promise:

promises are native to javascript so creation of promise object syncronous in nature

states and value is the property of promises

3 states of promise and 

1) pending ----> when we create a new promise object this is the default state. it represents work in progress

2) fullfield ---> if the operation is completed sucessfully 

3) rejected ---> if op was not successfull

How to create a new promise:

new Promise(f) ---->  () is a constructor and expects a callback function f

f is a executor function


new Promise(function (resolve, reject){
	// inside funjction we can write time consuming task

 // resolve(x);
 
})

if call resolve, the promise goes on fulfilled state 
if you call reject function it goes on a reject state
if you don't call anything, it remains in pending state

with whatever arguments we call resolve or reject with gets assigned to the value property




At the time when the constructor generates a new promise object, it also generates a pair of func, called as resolve and reject

generally the executor callbacks, wraps some async/sync operations

the executor is called sync

Consuming Promise:


let p = fetch(" ");

attach the functionality that we need to execute once the promise is fulfiled or rejected

p.then(fulfilmenthendler, rejectionhandler) takes two parameter
these are two handler function that we have to implement ourselves



value
state
onfulfilment:[]
onrejection:[]

using .then function we are regestring these two handler functions in the array





function getRandomInt(max) {
    return Math.floor(Math.random() * max);
}
function createPromiseWithTimeout() {
    return new Promise(function executor(resolve, reject) {
        console.log("Entering the executor callback in the promise constructor");
        setTimeout(function () {
            let num = getRandomInt(10);
            if(num % 2 == 0) {
                // if the random number is even we fullfill
                resolve(num);
            } else {
                // if the random number is odd we reject
                reject(num);
            }
        }, 1000);
        console.log("Exitting the executor callback in the promise constructor");
    });
}

console.log("Starting....");
const p = createPromiseWithTimeout();
console.log("We are now waiting for the promise to complete");
console.log("Currently my promise object is like ... ", p);
console.log("Going to register my 1st set of handlers");
p
.then(
    function fulfillHandler1(value) { 
        console.log("Inside fulfill handler 1 with value", value); 
        console.log("Promise after fullfillment is", p);
        setTimeout(function t() {console.log("Ended 0s timer")}, 0);
        console.log("exitting the full handler 1");
    }, 
    function rejectionHandler1(value) {  
        console.log("Inside rejection handler 1 with value", value); 
        console.log("Promise after rejection is", p);
        setTimeout(function t() {console.log("Ended 0s timer")}, 0);
        console.log("exitting the reject handler 1");
    }
);
console.log("Going to register my 2nd set of handlers");

p
.then(
    function fulfillHandler2(value) { 
        console.log("Inside fulfill handler 2 with value", value); 
        console.log("Promise after fullfillment is", p);
    }, 
    function rejectionHandler2(value) {  
        console.log("Inside rejection handler 2 with value", value); 
        console.log("Promise after rejection is", p);

    }
);

console.log("Ending......");
setTimeout(function () {console.log("Global timer of 0s")}, 1000);



settimeout creates new id every time

on the point of p.then 
value : undefined
state: pending
[] : onfulfilment[fh], onrejection[rh]

everythin is happened in the execution pahase





// microtaskque


function createPromise() {
    return new Promise(function exec(resolve, reject) {
        console.log("Resolving the promise");
        resolve("Done");
    });
}

setTimeout(function process() {
    console.log("Timer completed");
}, 0);

let p = createPromise();
p.then(function fulfillHandler1(value) {
    console.log("we fulfilled1 with a value", value);
}, function rejectHandler() {});
p.then(function fulfillHandler2(value) {
    console.log("we fulfilled2 with a value", value);
}, function rejectHandler() {});
p.then(function fulfillHandler3(value) {
    console.log("we fulfilled3 with a value", value);
}, function rejectHandler() {});

for(let i = 0; i < 10000000000; i++) {}

console.log("ending");


at any point of time if event loop has a choice to pick from microtaskque or call back que then it alwys give preference to micro task




// Demo1

function fetchData(url) {
    return new Promise(function (resolve, reject) {
        console.log("Started downloading from", url);
        setTimeout(function processDownloading() {
            let data = "Dummy data";
            resolve(data);
            console.log("Download completed");
        }, 7000);
    });
}

console.log("Start");
let promiseObj = fetchData("skfbjkdjbfv");
promiseObj.then(function A(value) {
    console.log("value is", value);
})
console.log("end");




// Demo2

console.log("Start of the file");

setTimeout(function timer1() {
    console.log("Timer 1 done");
}, 0);

for(let i = 0; i < 10000000000; i++) {
    // something
}

let x = Promise.resolve("Sanket's promise");
x.then(function processPromise(value) {
    console.log("Whose promise ? ", value);
});

setTimeout(function timer2() {
    console.log("Timer 2 done");
}, 0);

console.log("End of the file");




// Demo 3 

function blocking_for_loop() {
    for(let i = 0; i < 10000000000; i++) {
        // something
    }
}
console.log("Start of the file");
setTimeout(function timer1() {
    console.log("Timer 1 done");
}, 0);
blocking_for_loop();
let x = Promise.resolve("Sanket's promise1");
x.then(function processPromise(value) {
    console.log("Whose promise ? ", value);
    blocking_for_loop();
});
let y = Promise.resolve("Sanket's promise2");
y.then(function processPromise(value) {
    console.log("Whose promise ? ", value);
    setTimeout(function () {console.log("ok done")}, 0);
});
let z = Promise.resolve("Sanket's promise3");
z.then(function processPromise(value) {
    console.log("Whose promise ? ", value);
});
setTimeout(function timer2() {
    console.log("Timer 2 done");
}, 0);
console.log("End of the file");







// callbackdownloaderdummy
// problem IOC
function download(url, cb) {
    console.log("Started downloading from url", url);
    setTimeout(function exec() {
        console.log("Completed downloading after 5s");
        const content = "ABCDEF";
        // cb(content);
        // cb(content);
    }, 5000);
}


download("www.xyz.com", function processDownload(data) {
    console.log("downloaded data is", data);
})






// promisedownloaddummy
// solve IOC

function download(url) {
    console.log("started downloading content form ", url);
    return new Promise(function exec(res, rej) {
        setTimeout(function p() {
            console.log("COmpelted downloading data in 5s");
            const content = "ABCDEF";
            res(content);
        }, 5000);
    })
}

x = download("www.xyz.com");
x
.then(
    function fulfillHandler1(value) {
        console.log("Content downloaded is1", value);
        return "New promise string";
    },
    function rejectHandler1(value) {
        console.log("rejected with", value);
    }
)
.then(
    function newFullFillHandler(value) {
        console.log("value from chained then promsie", value);
    }
)



the .then returns a new promise object. it imediately returns a new promise object






//  promisechainingmdn

Promise.resolve("foo")
.then(function p1(string) {
        return new Promise((resolve, reject) => {
            setTimeout(() => {
                string += "bar"; //foobar
                resolve(string);
            }, 10000);
        })
    }
)
.then(function p2(string) {
    setTimeout(() => {
        string += "baz";
        console.log(string); // foobarbaz
    }, 1);
    return string; // foobar
})
.then(function p3(string) {
    console.log(string); // foobar
});






// promiseschaineddemo

Promise.resolve("foo")
.then(function fh1(value) {
    return Promise.resolve(value+"bar");
})
.then(function fh2(value) {
    setTimeout(function exec() {
        value+="baz";
        console.log(value);
        return 10;
    }, 1);
    // return value;
})
.then(function fh3(value) {
    console.log("from fh3", value);
})






// pain

Promise.resolve("foo")
  // 1. Receive "foo", concatenate "bar" to it, and resolve that to the next then
  .then(
    (string) =>
      new Promise((resolve, reject) => {
        setTimeout(() => {
          string += "bar";
          resolve(string);
        }, 1);
      }),
  )
  // 2. receive "foobar", register a callback function to work on that string
  // and print it to the console, but not before returning the unworked on
  // string to the next then
  .then((string) => {
    setTimeout(() => {
      string += "baz";
      console.log(string); // foobarbaz
    }, 1);
    return string;
  })
  // 3. print helpful messages about how the code in this section will be run
  // before the string is actually processed by the mocked asynchronous code in the
  // previous then block.
  .then((string) => {
    console.log(
      "Last Then: oops... didn't bother to instantiate and return a promise in the prior then so the sequence may be a bit surprising",
    );

    // Note that `string` will not have the 'baz' bit of it at this point. This
    // is because we mocked that to happen asynchronously with a setTimeout function
    console.log(string); // foobar
  });

// Logs, in order:
// Last Then: oops... didn't bother to instantiate and return a promise in the prior then so the sequence may be a bit surprising
// foobar
// foobarbaz








// callbackImpl

// Tasks: (Don't use promises only use callbacks)
// 1. Write a function to download data from a url
// 2. Write a function to save that downloaded data in a file and return the filename
// 3. Write a function to upload the file written in previous step to a newurl

function download(url, cb) {
    
      // Downloads content from the given url and passed the 
      // downloaded content to the given callback cb
     
    console.log("Starting to download data from", url);
    setTimeout(function down() {
        console.log("Downloading completed");
        const content = "ABCDEF"; // assume dummy download content
        cb(content);
    }, 10000);
}

function writeFile(data, cb) {
    
     // writes the given data into a new file
     
    console.log("Started writing a file with", data);
    setTimeout(function wrtie() {
        console.log("Completed writing the data in a file");
        const filename = "file.txt";
        cb(filename);
    }, 5000);
}

function upload(url, file, cb) {
    
     // uploads the data from a file to a given url
    
    console.log("Started uploading", file, "on", url);
    setTimeout(function up() {
        console.log("upload completed");
        const response = "SUCCESS";
        cb(response);
    }, 2000);
}

download("www.xyz.com", function processDownload(content) {
    console.log("We are now going to process the downloaded data");
    writeFile(content, function processWrite(filename) {
        console.log("We have downloaded and written the file, now will upload");
        upload("www.upload.com", filename, function processUpload(response) {
            console.log("we have uploaded with", response);
        });
    });
});







// promiseimpl

// Tasks: (Don't use callback only use promises)
// 1. Write a function to download data from a url
// 2. Write a function to save that downloaded data in a file and return the filename
// 3. Write a function to upload the file written in previous step to a newurl

function download(url) {
    return new Promise(function exec(resolve, reject) {
        console.log("Starting to download data from", url);
        setTimeout(function down() {
            console.log("Downloading completed");
            const content = "ABCDEF"; // assume dummy download content
            resolve(content);
        }, 6000);
    });
}

function writeFile(data) {
    return new Promise(function exec(resolve, reject) {
        console.log("Started writing a file with", data);
        setTimeout(function wrtie() {
            console.log("Completed writing the data in a file");
            const filename = "file.txt";
            resolve(filename);
        }, 5000);
    })
}

function uploadData(file, url) {
    return new Promise(function exec(resolve, reject) {
        console.log("Started uploading", file, "on", url);
        setTimeout(function up() {
            console.log("upload completed");
            const response = "SUCCESS";
            resolve(response);
        }, 2000);
    })
}

download("www.xyz.com")
.then(function processDownload(value) {
    console.log("downloading done with following value", value);
    return writeFile(value);
})
.then(function processWrite(value) {
    console.log("data written in the file with name", value);
    return uploadData(value, "www.upload.com");
})
.then(function processUpload(value) {
    console.log("we have uploaded with", value);
});
