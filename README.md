# vapor-hello-world

A Hello, world! server app written in [Swift](https://swift.org), using [Vapor](https://vapor.codes), deployable on [Heroku](http://heroku.com).

## Requirements

- Xcode (which delivers swift)
- [vapor](https://docs.vapor.codes/3.0/install/macos/)
- [heroku cli](https://devcenter.heroku.com/articles/heroku-cli)

> Try `brew install vapor/tap/vapor heroku-cli`

## Create from scratch

```sh
# start new Vapor project
vapor new HelloWorld
pushd HelloHelloWorld
vapor xcode # I had to run this twice, first time I got a bunch of LibreSSL errors about not being able to connect to GitHub to download the dependencies
rm -rf .git # vapor starts a git repo inside the project folder, but this project is inside a repo already!

echo "4.1.1" > .swift-version

# make Procfile for Heroku
echo "web: Run serve --env production --hostname 0.0.0.0 --port \$PORT
local: .build/debug/Run serve --env production --hostname 0.0.0.0 --port 8080" > Procfile
```

> At this point, the app is ready, but it has two pages and some example models and controllers, and a SQLite database connection. To simplify to a barebones Hello, world!, open the Xcode project and make the same edits as [this commit](https://github.com/armcknight/vapor-hello-world/commit/d26713fb2e5e0ddc352316a7ad9b5e30a974da68).

```sh
vapor build
popd
```

## Deployment

### Local

```sh
pushd HelloWorld
vapor run serve & # or run the `Run` scheme in Xcode.
popd
open http://localhost:8080
```

### Locally with Heroku

```sh
heroku local local &
open http://localhost:8080
```

### Remote

```sh
heroku create --buildpack https://github.com/vapor-community/heroku-buildpack.git # vapor/vapor is supposed to be the stable release but currently doesn't work
heroku stack:set heroku-16 -a <app-name> # the buildpack doesn't work on the current default stack heroku-18, so we must downgrade
git subtree push --prefix HelloWorld heroku master # heroku wants everything to be in the root directory, but I don't wanna
heroku open
```

## References

- [Vapor macOS](https://docs.vapor.codes/3.0/install/macos/)
- [Vapor Hello, world](https://docs.vapor.codes/3.0/getting-started/hello-world/)

> References are preserved as PDFs in `docs/`.