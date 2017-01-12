---
layout: post
title:  "Use Docker for your dependcy services - get benefit without dockerizing you app"
date:   2017-01-07 10:00:00
tags: docker mysql postgres redis
---

I have seen tons of articles on how to use Docker with your application,
but most of them are focused around dockerizing your app.

It's all nice and good, but not everyone is ready to jump into it,
or have enough spare time to learn how to do it.

So I suggest another way to start using Docker and Docker Compose, which

* can provide benefits right now

* doesn't require that much time to learn

* can be a nice way to learn working with Docker gradually

# Wait, why? And what kind of benefits are you talking about?

Chances are, as a developer, you are involved into many projects simultaneously,
which may require different versions of these dependency services.

It can be because of:

* Hobby projects. Who doesn't have some kind of hobby project? :)

* Tech exploration projects. You may want to check out that new fancy features
present in newest version of DBMS you use, or check out new system.

* Working as freelancer or in outsource company.

* Working on a microservice/service-oriented-architecture project, with a lot of
different services, which can sometimes require different versions of services.
While it's not really good, this can happen in real world.

* Insert your own reason here. Mail me with your reason (or, even better,
the link on blog post where you go in length about it) and I can mention it here.

Even if these cases don't strictly require you to use exactly the same version,
using versions different to what is used on production (or whatever you call it
in case of hobby/exploration project) can cause subtle and really annoying bugs.

So it's generally recommended to keep development environment as much in sync
with production as possible.

And here comes the tricky part: on most OSes I've seen, having multiple
versions of same software can be problematic at best, not partically possible
at worst.

# Docker Compose to the rescue!

You can easily start using Docker Compose to help you spin up multiple versions
of services your app needs. I will illustrate it using PostgresQL 9.2 as an
example. At the time of writing it's already a pretty old version,
and, official repos of Arch Linux, for instance, provide only 9.6.1.

## 0. Install docker and docker-compose (of course)

[Here is the official guide][installing-docker-compose] for installing
docker-compose. It includes installing Docker.

I use Arch Linux, so I just use the one provided in official repos:

```
pacman -S docker docker-compose
```

Please note, in some of the repos you might find pretty old versions of
`docker-compose`. For instance, at the time of writing, in Ubuntu repos
(both 16.04 and 16.10) it's `1.5.2`, when "up-to-date" release is `1.9.0`.

## 1. Prepare your docker-compose.yml

_(Skip this step if you already have such file for services)_

Docker Compose searches for `docker-compose.yml` in a similar way that
git searches for root of the repo.

So, if you call the `docker-compose`, it will check the current directory for
the compose file, and if it's not there, it will check parent folders till
it either finds it or reaches to the root of the file system.

So, to run the all `docker-compose` commands from examples you will have to be
in the directory where `docker-compose.yml` is located or in any of its own
subdirectories.

Create somewhere file called `docker-compose.yml` and put the barebones there.
We will not have there any services defined at this point - see the next steps
for adding a new service definition to this file.

```
version: '2'
services:
```

You can use one file for all your services you want to spin up this way.

Note, that if any of your projects use docker-compose for something,
it's better to create a new file decidated only to your own services.

## 2. Find an image for the service you want

For this you will probably have to go to [Docker Hub][dockerhub] and search
there.

I prefer to use official images, but if you want to use something without
an official image available, you probably can use something provided by other
people you trust enough.

I will use [official postgres image][dockerhub-postgres] for this example.

## 3. Add a service you need

So, let's say, I want to add Postgres 9.2 image that I found on Dockerhub and
make it available at host `127.0.0.1` and port `15432`.

Then I need ot add service definition to `services` section, like this:

```
version: '2'
services:
  postgres-9.2:
    image: postgres:9.2
    env:
      - POSTGRES_PASSWORD=postgres_password
      - POSTGRES_USER=postgres_user
    ports:
      - '127.0.0.1:15432:5432'
```

Explaination of options used:

* `postgres-9.2` - name of the service, will be used later to start and stop it.

* `image: postgres:9.2` - image to pull from DockerHub, in format `name:version`.

* `env:` - environment variables to set inside the service. Array, one per line,
in format `NAME=value`.

* `ports:` - which ports share to the current machine and to what map them.
Array of strings with format `host_ip:host_port:port_inside_container`.

[Compose file reference][compose-file-reference] contains more options
you can use to customize your service.

Note, that you have [the whole 127.x.y.z/8 block of IPv4][loobpack-addresses]
addressess that all are bound to your "loopback" device and, basically, mean
"the same computer". It's 16387064 addressess you can use if you want.
And each of that addressess have ~65k TCP ports you can bind your services to. :)

## 4. Get it started

In the directory where you have your `docker-compose.yml` file run:

```
docker-compose up postgres-9.2
```

This will behave like a regular foreground CLI app - print output to the console,
stop by `CTRL+C` and so on.

If you want to make it go to background, there is an option for it - `-d` (for
"detach"):

```
docker-compose up -d postgres-9.2
```

In this case you can still see the logs whenever you want:

```
docker-compose logs postgres-9.2
```

It even supports `-f`/`--follow` option, that will make it behave like
`tail -f`.

## 5. Connect and use!

Now you can point PostgresQL client (like, for instance, you app) to the
`127.0.0.1:15432`, use `postgres_user` as user and `postgres_password` as
a password, and and it will connect to your newly brought up PostgresQL 9.2.

## 6. Stop

If you've used the `-d` option, or want to stop it from the other
terminal, you can use the `stop` command:

```
docker-compose stop postgres-9.2
```

If you've not used the `-d` option, just press `CTRL+C` once and wait for
the container to stop.

# More useful commands

* `docker-compose ps -a` - to show the state of all containers associated with
the definitions in compose file.

* `docker-compose run --rm postgres-9.2 /bin/bash` - to start bash terminal
inside the container.

[And more][compose-cli-reference].

# More examples

[Here][github-services] is my repo with collection of services you can just
clone and use. It haven't been updated for a while, but still can be used as an
example.

You may want to share the service definition that was useful to you, for
instance, by putting your services file to the git repo and pushing it
to Github. Or you can make a pull-request for this repo that I have. :)

# P.S.

As always, I would be glad to get your [feedback][about-feedback] about this
post.

[github-services]: https://github.com/ivan-kolmychek/services
[installing-docker-compose]: https://docs.docker.com/compose/install/
[dockerhub]: https://hub.docker.com/
[dockerhub-postgres]: https://hub.docker.com/_/postgres/
[compose-file-reference]: https://docs.docker.com/compose/compose-file/
[about-feedback]: /about/#feedback
[loopback-addresses]: https://en.wikipedia.org/wiki/Localhost#Name_resolution
[compose-cli-reference]: https://docs.docker.com/compose/reference/
