# Webpack XBlocks
The purpose of this repository is to house scripts for allowing quick conversion of an xblock
repository to use webpack builds, thus enabling use of ES6 syntax, React, and the Paragon
component library.

## package.json
The first file you will need to add is a package.json file describing your project.
The included example provides a basic implementation, which provides access to edx frontend
build scripts, along with react, redux, paragon, and axios.

You should make sure to update the name and description of your package, as well as the lint path.

## env.yml
This file defines a set of environment files for various build environments.  To generate an .env
file for the chosen environment, run `dotenvi -s <environment>`.
environment variables prepended with `REACT_APP_` will be accessible in react JS as
`process.env.REACT_APP_<...>`.

Right now, the only active target is the `production` build environment.

## webpack.prod.config.js
This file extends the edx webpack build configuration for our Micro-Frontends.
In this file, you should be careful to explicitly update:
  * L15: The entry name.  This will determine the built filenames
  * L18: The entry path.  This should point to your root js library.
  * L23: The output path.  This should point to your output static dist folder.
  * L41: The code path for local imports.  This should point to your static js source
         folder.

## Integration
From there, you just need to make sure that your xblock code adds the root html file and
built JS/CSS files.

  * `static/public/index.html` __not built__
  * `static/dist/<entry_name>.js`
  * `static/dist/<entry_name>.css`
