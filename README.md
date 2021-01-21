# Toodles

[![Build Status](https://travis-ci.org/aviaviavi/toodles.svg?branch=master)](https://travis-ci.org/aviaviavi/toodles)
[![Hackage](https://img.shields.io/hackage/v/toodles.svg)](https://hackage.haskell.org/package/toodles)
[![Scarf](https://scarf.sh/package/badge/toodles)](https://scarf.sh/package/avi/toodles)
[![Gitter chat](https://badges.gitter.im/gitterHQ/gitter.png)](https://gitter.im/toodles-todos/community)

Toodles scrapes your entire repository for TODO entries and organizes them so
you can manage your project directly from the code. View, filter, sort, and edit
your TODO's with an easy to use web application. When you make changes via
toodles, the edits will be applied directly the TODO entries in your code.
When you're done, commit and push your changes to share them with your team!

![Toodles Screenshot](https://i.imgur.com/DEwzMYn.png)

### TODO details

Specify details about your TODO's so that you can filter and sort them with
ease! Specify details within parenthesis and separate with the `|` delimeter.

```python
# TODO(assignee|p=1|keys=vals|#tags)
```

#### Priority

The key `p=<integer>` will be interpreted as a priority number

#### KeyVals

Use arbitrary key value pairs `<key>=<value>|<key2>=<value2>|...` and design any
organization scheme you wish! A good use for this is to enter dates of deadlines
for TODO's that you can sort on in Toodles

#### Tags

A detail starting with `#`, eg `#bug|#techdebt|#database|...` will be interpreted as
a tag, which can be used to label and group your TODO's.

#### Assign

Assign your TODO's to someone. Any plain word that will be interpreted as an assignee.

```python
# TODO(bob) - something we need to do later
```

### Per Project Configuration

You can configure toodles by putting a `.toodles.yaml` file in the root of your
project. See this repo's `.toodles.yaml` for the full configuration spec.

Currently via config you can:

- Set files to ignore via a list of regular expressions
- Specify your own flags to scan for other than the built-ins (TODO, FIXME, XXX)

#### Ignoring Files

Ignore as many files as you can! Large autogenerated files will slow Toodles
down quite a bit. Check the output of the server to see any files/folders that
may be causing slowness for your repo and add them to the `ignore` section your
`.toodles.yaml` If the performance of Toodles is not good enough for your use
case, please open an issue.

### Scanned Languages

These languages will be scanned for any TODO's:

- C/C++
- C#
- CSS/SASS
- Elixir
- Erlang
- Go
- Haskell
- HTML
- Java
- Javascript
- Kotlin
- Lua
- Objective-C
- PHP
- Plaintext files (`*.txt`)
- Protobuf
- Python
- React Javascript (JSX)
- Ruby
- Rust
- Scala
- Shell / Bash
- Swift
- Typescript
- Vue (scripts only)
- Yaml

Submit a PR if you'd like a language to be added. There will eventually be
support for this to be user configurable

### Installing with Scarf

[Scarf](https://scarf.sh) is the easiest way to get Toodles.

```bash
$ scarf install toodles
```

### Installing with Docker

You can run a pre-built toodles for your current directory via docker:

```bash
# execute toodles for the directory you are currently in:
$ docker run -it -v $(pwd):/repo -p 9001:9001 docker.avi.press/aviaviavi/toodles
```

Just mount your project into the container's `/repo` and direct a port of your
choice to the container's `9001`.

### Building Toodles

Toodles builds with  [stack](https://docs.haskellstack.org). Just a `stack
build` should do it. If you'd like to build toodles without cloning the source,
you can have stack build toodles with `stack install --resolver=lts-12.14 toodles`!

#### Building with Docker

For convenience this repository also provides a `Dockerfile` to automatically
build toodles.

```bash
# to build container run:
$ cd /path/to/toodles/repo
$ docker build -t toodles Dockerfile.dev .
# afterwards you can run the following command to execute toodles for the
# directory you are currently in:
$ docker run -it -v $(pwd):/repo -p 9001:9001 toodles

```

### Running

Invoking `toodles` with no arguments will treat the current directory as the
project root and will start a server on port 9001. You can set these with the
`-d` and `-p` flags, respectively.


```bash
# $ toodles -d <root directory of your project> -p <port to run server>
# for more info run:
# $ toodles --help
$ toodles -d /path/to/your/project -p 9001
# or simply
$ toodles
```

### Contributing

If Toodles is useful to you or your organization, please consider supporting the project 
by purchasing Toodles on [Scarf](https://scarf.sh/package/avi/toodles).

Contributions in any form are welcome! A few bits of info:

- Don't be shy, ask questions! Contributing to Toodles should be welcoming for
  people at any level of programming familiarity. Whether it's a new feature,
  bug fix, or docs, any contribution is very appreciated.
- Open an issue or jump into the chat room on [gitter](https://gitter.im/toodles-todos/community)
- Before you start coding, please comment or mark a particular issue as "in
  progress", or even open your pull request as a work in progress (WIP). This is
  to help avoid having multiple people work on the same thing.
- If github issues don't cut it, feel free to reach out on gitter or twitter
  [@avi_press](https://twitter.com/avi_press)
