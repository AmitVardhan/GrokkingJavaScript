### export

The export statement is used when creating JavaScript modules to export live bindings to functions, objects, or primitive values from the module so they can be used by other programs with the import statement. The value of an imported binding is subject to change in the module that exports it. When a module updates the value of a binding that it exports, the update will be visible in its imported value.

Notes:
1. Exported modules are in strict mode whether you declare them as such or not. 
2. The export statement cannot be used in embedded scripts.
3. You need to include this script in your HTML with a <script> element of type="module", so that it gets recognized as a module and dealt with appropriately.
4. You can't run JS modules via a file:// URL — you'll get CORS errors. You need to run it via an HTTP server.

There are two types of exports:
	1. Named Exports (Zero or more exports per module)
	2. Default Exports (One per module)
	
Named Exports
```javascript
// module "my-module.js"
function cube(x) {
  return x * x * x;
}

const foo = Math.PI + Math.SQRT2;

var graph = {
  options: {
      color:'white',
      thickness:'2px'
  },
  draw: function() {
      console.log('From graph draw function');
  }
}

export { cube, foo, graph };
```

You can import it as
```javascript
import { cube, foo, graph } from './my-module.js';

graph.options = {
    color:'blue',
    thickness:'3px'
};

graph.draw();
console.log(cube(3)); // 27
console.log(foo);    // 4.555806215962888
```
