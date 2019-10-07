# projectES6

https://www.freecodecamp.org/news/a-practical-es6-guide-on-how-to-perform-http-requests-using-the-fetch-api-594c3d91a547/

https://www.freecodecamp.org/news/how-to-make-a-promise-out-of-a-callback-function-in-javascript-d8ec35d1f981/

https://codingthesmartway.com/async-programming-with-javascript-callbacks-promises-and-async-await/

https://www.smashingmagazine.com/2019/02/node-api-http-es6-javascript/

https://medium.com/front-end-weekly/callbacks-promises-and-async-await-ad4756e01d90

https://codeburst.io/a-simple-guide-to-es6-promises-d71bacd2e13a

https://dev.to/ccleary00/how-to-rewrite-a-callback-function-in-promise-form-and-asyncawait-form-in-javascript-410e

https://medium.com/@samthor/js-callbacks-to-promises-541adc46c07c

https://scotch.io/courses/10-need-to-know-javascript-concepts/callbacks-promises-and-async

------------------_----------------


https://restfulapi.net/http-methods/

https://www.restapitutorial.com/lessons/httpmethods.html

https://stackify.com/rest-api-tutorial/


https://www.tutorialspoint.com/reactjs/reactjs_components.htm

https://www.youtube.com/watch?v=HaEGyA91auk&list=PLu6MFGxDdiliq6MH-rBxOu46TksEKsUP0&index=3
const USERS = 'https://jsonplaceholder.typicode.com/users';
const COMM = 'https://jsonplaceholder.typicode.com/comments';
const POST = 'https://jsonplaceholder.typicode.com/posts';

const root = document.getElementById('root');
class FistClass {
    constructor(elementId) {
        this.elementId = elementId;
      }

      /** FETCH **/
      getData(uri){
        fetch(uri)
        .then((response) => { console.log(response); return response.json()})
        .then((data) => {
            //console.log('ds' ,data);
            //root.innerHTML = `${JSON.stringify(data)}`;
            this.appendData(data);
        })
      }

      /** ASYNC AWAIT **/
      async getDataAsync(uri){
          const response = await fetch(uri);
          const data = await response.json()
          //console.log('got a response', json)
          this.appendData(data);
    }

    appendData (data){
    for (var i = 0; i < data.length; i++) {
                var div = document.createElement("div");
                div.style.marginTop = "15px";
                div.innerHTML = `ID: ${data[i].id} <br> Name: ${data[i].name} <br> Username: ${data[i].username}
                <br> Email: ${data[i].email} <br> Address: street: ${data[i].address.street} suite: ${data[i].address.suite} city: ${data[i].address.city} <br> zipcode: ${data[i].address.zipcode} <br> geo: lat: ${data[i].address.geo.lat} long: ${data[i].address.geo.lng}<br> Phone: ${data[i].phone}
                <br> Website: ${data[i].website} <br> Company: name: ${data[i].company.name} catchPhrase: ${data[i].company.catchPhrase} bs: ${data[i].company.bs}`;
                root.appendChild(div);
            }
        }

}


const app = new FistClass('root');
//app.getData(USERS);
app.getDataAsync(USERS);
