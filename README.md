# JS-Objects
## property flags, freeze(), seal, preventExtensions in java Script
🔹 Property Flags

Each object property in JavaScript has attributes/flags that define how it behaves. These are known as property descriptors:

writable

true: the property value can be changed.

false: the property value is read-only.

enumerable

true: the property shows up in loops like for...in or Object.keys().

false: the property is hidden from enumeration.

configurable

true: the property can be deleted or changed.

false: it cannot be deleted or redefined.

👉 You can check them using:

let obj = { name: "Dhanu" };
console.log(Object.getOwnPropertyDescriptor(obj, "name"));

🔹 Object.preventExtensions(obj)

Prevents adding new properties to an object.

Existing properties remain editable and removable.

let obj = { a: 1 };
Object.preventExtensions(obj);
obj.b = 2; // ❌ ignored
console.log(obj); // { a: 1 }

🔹 Object.seal(obj)

Prevents adding new properties ❌.

Prevents deleting properties ❌.

Still allows modifying existing property values ✅ (if writable).

let obj = { a: 1 };
Object.seal(obj);
obj.b = 2; // ❌ ignored
delete obj.a; // ❌ ignored
obj.a = 10; // ✅ allowed
console.log(obj); // { a: 10 }

🔹 Object.freeze(obj)

Prevents adding ❌, deleting ❌, or modifying properties ❌.

Makes the object completely immutable (shallow freeze).

let obj = { a: 1 };
Object.freeze(obj);
obj.a = 10; // ❌ ignored
delete obj.a; // ❌ ignored
console.log(obj); // { a: 1 }

🔹 Comparison Table
Feature	preventExtensions	seal	freeze
Add new properties	❌ No	❌ No	❌ No
Delete properties	✅ Yes	❌ No	❌ No
Modify existing values	✅ Yes	✅ Yes	❌ No
Change property flags	✅ Yes	❌ No	❌ No
