# Installation


## Requirements

- Node >= 14

## Prerequisites

Before we start, we'll assume we have a working installation of GetCandy ready to go. If you haven't installed GetCandy yet, it's strongly recommended you do so first and then come back.

We're also going to assume our store is called clothing-store for the API and Hub. So we're going to assume our directories are set up as follows:

```
| clothing-store
|-- api
|-- hub
```

<alert>
For this installation we're going to be using Sanctum for API authentication.
</alert>

## Installing the hub

The Admin Hub is a Nuxt.js SPA, so knowledge of how it works is beneficial but not required to get it installed. We have created a repo for you to clone down which is pre-configured.

Create the directory you wish the hub reside if it doesn't exist already

```shell
mkdir hub && cd hub
```

Clone down the hub repository

```shell
git clone https://github.com/getcandy/hub.git  .
```

Copy the example .env file

```shell
cp env.example .env
```

The values in here should be set up for running artisan serve on our API. We'll get to that.

Install the dependencies

```shell
yarn install
```

### Starting the API

If you look in the .env file you'll see something like:

```yaml
API_BASE=http://localhost:8000/api/v1
```

For Sanctum to work, we want the hub and the API to run off the **same domain**. So open up a new terminal window/tab and `cd` into your Laravel API directory (not the hub), we want to start the development server on `localhost`.

```shell
php artisan serve --host=localhost
```

This will boot up our API on `localhost:8000` so keep that tab open on your terminal. Now back in the hub directory, we can start the hub up.

```shell
yarn dev
```

If everything has gone to plan. You should now see the login page for the hub on `localhost:3000`

### What's Next

Getting issue's after installing? See if our troubleshooting page can get you going again.
