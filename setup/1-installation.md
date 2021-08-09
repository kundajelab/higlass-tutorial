# Step 1: Installation
Before we can use HiGlass, we need to install the latest versions of both its frontend ([`higlass`](https://github.com/higlass/higlass)) and backend ([`higlass-server`](https://github.com/higlass/higlass-server)).

There are two options for installation: using a Docker image or manually installing each component. Docker installation is generally easier and faster than manual installation, but it makes local development on HiGlass much more difficult, does not allow you to edit the view config, and will typically install a version of HiGlass that is a few months out of date.

If you are deploying HiGlass to a server to showcase your work and don't want to change the default appearance of HiGlass, Docker will usually be the better choice. However, if you want to embed HiGlass in a separate webpage, need a very recent version of HiGlass, or want to develop on HiGlass, you must use the manual installation method.

## Docker installation:
TBD

## Manual installation:

### Prerequisites
Before installing HiGlass, make sure you have the prerequisites. If you followed the [GCP Setup guide](./0-gcp-setup.md) or have a system running a recent version of Ubuntu, you will only need to run this command:

```sh
sudo apt install python3-pip libcurl4-gnutls-dev nginx
```
Otherwise, you will need:

- An installation of Python 3.4+ (check out [this guide](https://realpython.com/installing-python) if you don't have it)
  - Make sure you also have `pip3` installed. If it's not already available, use [this guide](https://pip.pypa.io/en/stable/installation/). On Debian-based Linux distros (e.g. Ubuntu) you will probably need `python3-pip`.
- An installation of Node.js (try [this guide](https://nodejs.org/en/download/package-manager/) if you don't have it)
  - Some Linux distros come with `node` but not `npm`: you need both, so follow the guide above if you don't have `npm`.
- An installation of `curl` and `curl-config` (on Debian-based distros, the `libcurl4-gnutls-dev` package has it)
- An installation of `nginx` (follow [this guide](https://www.nginx.com/resources/wiki/start/topics/tutorials/install/))

### Backend

#### `higlass-server`
You will need to clone the `higlass-server` repository first. Run the following:

```sh
git clone https://github.com/higlass/higlass-server.git
cd higlass-server
```

Now you should install the dependencies. In theory you would just run `pip3 install -r requirements.txt`, but that will probably not work on a clean installation because some of the dependencies are very out of date as of the time of writing. Therefore, try running:

```sh
pip3 install $(sed 's/==.*//g' requirements.txt)
```

#### `clodius` (local install only)
If you're developing on Clodius and/or need the master branch of Clodius, you can manually install it as so:

```sh
cd ..
git clone https://github.com/higlass/clodius.git
pip3 install ./clodius
cd higlass-server
```

#### Validating server installation

Try running the following command:

```sh
python3 manage.py migrate
```

If you see a row of "OK", you've installed the server properly. Now, when you want to run the server, you can just do:

```sh
python3 manage.py runserver localhost:8080
```

### Frontend

If you want to use the bleeding-edge version of HiGlass, you should also run the following:

```sh
# If you just ran the backend setup:
# cd ..
git clone https://github.com/higlass/higlass
cd higlass
npm install
npm compile
```

In the `build/` directory, you should now see a few files, most importantly `hglib.min.js` and `hglib.css`. If you see them, you're done with most of the installation and can now start working on implementing HiGlass into your site.

For more information on tileset installation, embedding HiGlass, etc., continue with the [management section](./2-management.md).