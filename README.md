# vapor-hello-world

A Hello, world! server app written in [Swift](), using [Vapor](), deployable on [Heroku]().

## Requirements

- Xcode (which delivers swift)
- [vapor]()
- [heroku-cli]()

> Try `brew install vapor/tap/vapor heroku-cli`

## Create from scratch

```sh
# start new Vapor project
vapor new HelloWorld
pushd HelloHelloWorld
vapor xcode # I had to run this twice, first time I got a bunch of LibreSSL errors about not being able to connect to GitHub to download the dependencies
rm -rf .git # vapor starts a git repo inside the project folder, but this project is inside a repo already!
popd
```

Open the Xcode project and make out the edits from commit #d26713f.

```sh
vapor build
vapor run serve & # or run the `Run` scheme in Xcode.
open http://localhost:8080
```

## References

- [Vapor macOS](https://docs.vapor.codes/3.0/install/macos/)
- [Vapor Hello, world](https://docs.vapor.codes/3.0/getting-started/hello-world/)

> References are preserved as PDFs in `docs/`.