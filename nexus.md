# Private npm registry
The private registry is made up of three repositories in [nexus](http://nexus.livspace.com/#admin/repository/repositories):

 :fire::fire: The following urls have changed. Please update accordingly.
 1. ~~http://nexus.jx.livspace.com/repository/livspace-npm/: Private hosted npm repository that has all privately published packages.~~
 2. ~~http://nexus.jx.livspace.com/repository/npm-proxy/ : Proxies the public npm repository.~~
 3. ~~http://nexus.jx.livspace.com/repository/npm-group/ : Aggregator for both of the above so that you can download/search in the combined repository.~~

 The new urls are as follows:
 1. ~~http://nexus.livspace.com/repository/livspace-npm/: Private hosted npm repository that has all privately published packages.~~
 1. https://nexus.livspace.com/repository/livspacenpms3/: Private hosted npm repository that has all privately published packages.
 2. http://nexus.livspace.com/repository/npm-proxy/ : Proxies the public npm repository.
 3. http://nexus.livspace.com/repository/npm-group/ : Aggregator for both of the above so that you can download/search in the combined repository.

## Usage
Authentication can be done at the command line or using `.npmrc` file. Use `npmrc` package to manage different registries.  The following commands will install npmrc and setup `download` and `publish` profiles for search/download and publishing of packages respectively.

```
npm install -g npmrc
npmrc
npmrc -c download
npmrc download
npm config set registry http://nexus.livspace.com/repository/npm-group/ 
npmrc -c publish
npmrc publish
npm config set registry http://nexus.livspace.com/repository/livspace-npm/
```

You have to login in order to do further operations:
```
npmrc work 
```

## Login using credentials manually
__Note that you may not be able to login if you are running some specific versions of npm. This version works: 5.0.0__
To install this version on your system run
```
sudo npm i -g npm@5.0.0
```
Issue the login command and supply your credentials.

```
npm login
```
To search/install packages:
```
npm search vuejsonschema
npm i vuejsonschemaform
```

To publish your package to the private registry:
```
npmrc publish
npm publish
```

## Using .npmrc
Use the following command to generate the npm token:
```
echo -n 'username:password' | openssl base64
```
In your `~/.bash_profile` export the NPM_TOKEN
```
export NPM_TOKEN="<your_npm_token>"
```
Make a `.npmrc` file in your project root and add the following. Do not commit this file as the token shouldn't be pushed:
```
email=you@example.com
always-auth=true 
_auth=${NPM_TOKEN}
```
Edit your package.json to include the publish config:

```
"publishConfig"  : 
	{  
		 "registry"  :  "http://nexus.livspace.com/repository/livspace-npm/"  
	},
```
