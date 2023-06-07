---
published: true
---
/*
array can be very long. each element generate a webpage.
generate a webpage, which has 1 main image and 8 relative image
*/
  
## m1
let main = arr[0];
let relatives = arr.slice(1, 8 % len() + 1); //get subarray from arr[1] to arr[8]
generate_page(main, relatives);

let main = arr[1];
let relatives = arr.slice(2, 9 % len() + 1); //get subarray from arr[2] to arr[9]
generate_page(main, relatives);

...

//???
let main = arr[4];
let relatives = arr.slice(5, 12 % len() + 1); //get subarray from arr[5] to arr[1]
generate_page(main, relatives);


wrong!


## m2

var arr = [{id:1, name:'name'},{id:2, name:'name'},{id:3, name:'name'}];

for (let i = 0; i < arr.length; i++) {
  let main = arr[i];
  let relatives = [...arr]; //clone arr
  relatives.splice(i,1); //remove a element
  console.log(relatives);
}