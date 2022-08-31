# 🥞 Pancake Frontend

This project contains the main features of the pancake application.

If you want to contribute, please refer to the [contributing guidelines](./CONTRIBUTING.md) of this project.

## Documentation

- [Info](doc/Info.md)
- [Cypress tests](doc/Cypress.md)


## Quick Start

install dependencies using **yarn**

```sh
yarn
```

start the development server
```sh
yarn dev
```

build with production mode
```sh
yarn build

# start the application after build
yarn start
```
(In order of how I got everything setup step by step)

Download frontend, toolkit, and sdk then extract all 3 in the same folder.
Launch my router, factory, cake token, Masterchef, Syrup contracts without any changes. Then verify each contract.
3 Install each project (frontend, toolkit, & sdk) using "yarn install".
Change factory address and INIT_CODE_HASH in (sdk root>src>constants) then build the project with "yarn build".
Copy the dist file created in the root folder into the front end folder (front end> node_modules>@pancakeswap>sdk) .
Now we have a working trading system that runs on my own factory and router. You can do anything at this point from trading to selling and adding liquidity to tokens.

Steps to reproduce crash on farming:

Make sure all values and addresses punched into the contracts are set correctly.
Change masterchef contract address from "Panckeswaps" to ours. (front end>src>config>constants>contracts.ts)
Reload home page.
As page reloads everything looks normal until the profile located at the top starts to load then we are presented with a crash.
Expectations
I had assumed changing this value alone would be enough to redirect values to my Masterchef contract. If anyone can assist me with figuring this out that would be awesome.

Note: I did add the liquidity tokens into the masterchef "add" function to see if this would resolve the issue. Normally I would not be able to add anything to a farm without getting the error "Do you add enough gas?" but that is after I hit "activate farm" then "Stake".

Update:

I managed to get everything up and running! What I was missing was the hooks.ts file. Within it you can find pid 251 and 252. Changing these to match both my cake-busd and bnb-busd as well as changing the cake token address within tokens.ts managed to fix all of my issues. Tho some of my tokens will not display their APR 3 will however.
