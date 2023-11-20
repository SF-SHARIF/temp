


function sf_splice(array, start, deleteCount) {
    let result = [];
    let removed = [];
    let argsLen = arguments.length;
    let arrLen = array.length;


    // ইনপুট নেওয়ার সময় যদি string নাম্বার চলে আসে তাকে numbar এ নিয়ে নিয়ে আসার জন্য
    start = parseInt(start, 10);
    deleteCount = parseInt(deleteCount, 10);

    // start নাম্বার ভ্যালু যদি নেগেটিভ হয়ে যায়
    if (start < 0) {
        start = arrLen + start;
        start = (start > 0) ? start : 0;
    } else {
        start = (start < arrLen) ? start : arrLen;
    }

    // যদি ডিলিট করা সংখ্যা নেগেটিভ হয়ে যায়
    if (deleteCount < 0) {
        deleteCount = 0;
    }

    // array.length এবং start দুইটা বিয়োগ করার পর যদি ডিলেট এর সংখ্যা বড় হয় তাহলে
    if (deleteCount > (arrLen - start)) {
        deleteCount = arrLen - start;
    }

    // start করা জায়গা থেকে আগে সংখ্যাগুলো একটি array মধ্যে স্টোর করা
    for (let i = 0; i < start; i++) {
        result[i] = array[i];
    }

    //  argument নতুন ভ্যালুগুলো array মধ্যে যুক্ত করা |
    for (let i = 3; i < argsLen; i++) {
        result.push(arguments[i]);
    }

    // start and delete এরপরের ভ্যালুগুলো সব একসাথে করা
    for (let i = start + (deleteCount || 0); i < arrLen; i++) {
        result.push(array[i]);
    }



    // delete value গুলো নতুন একটা array মধ্যে স্টোর করা 
    for (let i = start; i < start + deleteCount; i++) {
        removed.push(array[i]);
    }


    // Update original array
    array.length = 0;
    let i = result.length;
    while (i--) {
        array[i] = result[i];
    }

    // Return array of removed elements
    return removed;
}


let arr = [1, 2, 3, 4, 5, 6, 7, 8, 9]

let r = sf_splice(arr, 7, 1, 'x', 'y')

console.log(arr);
console.log(r);



