This is an experiment to figure out why adding `remapping: [ "@openzeppelin=node_modules/@openzeppelin" ]` to the truffle-config.js breaks compiling of @openzeppelin.
Basically truffle does its own resolution of files under node_modules and builds its own standard json object. See truffle_compiler_input.json for an example. But basically:

1. Any file under "node_modules/PKG_NAME/..." appears as 
{
   sources: {
	   ...
	   "PKG_NAME/...": { ... }
   }
}

2. Any file under "contracts/...." appears as

{
   sources: {
	   ...
	   "project:/contracts/...": { ... }
   }
}
