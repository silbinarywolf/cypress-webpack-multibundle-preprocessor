# Cypress Webpack Multibundle Preprocessor

[![Build Status](https://api.travis-ci.org/silbinarywolf/cypress-webpack-multibundle-preprocessor.svg?branch=master)](https://travis-ci.org/silbinarywolf/cypress-webpack-multibundle-preprocessor)
[![npm Version](https://img.shields.io/npm/v/cypress-webpack-multibundle-preprocessor.svg)](https://www.npmjs.com/package/cypress-webpack-multibundle-preprocessor)

Cypress preprocessor for bundling JavaScript via webpack.

This differs from the [official implementation](https://github.com/cypress-io/cypress-webpack-preprocessor) as it will compile/bundle all spec tests found in the `cypress/integration` folder only once when you call `cypress run`, rather than run a seperate Webpack build per spec file.

The reason we want this is because we use Cypress as a [unit testing tool](https://github.com/silbinarywolf/cypress-aurelia-unit-test), which means each spec test imports the main codebase, this causes building each spec to take 60+ seconds each.

## Known Limitations

- Hardcoded to find all specs in `cypress/integration`, this is because Cypress currently assumes you only want to compile the spec right before it's execution and only provides the spec filepath to compile at that point in time.
- Bundling all specs at once only occurs if not in interactive / watch mode. The code for watch mode is identical to how the official implementation works.
