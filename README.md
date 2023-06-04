# PeaceFounderDemo
This is a demo of a PeaceFounder voting system intended to show capabilities, encourage experimentation and collect feedback for steering the development. This repository can also be used as a template for configuring your deme setup. If you do so:

- You will need to choose a name and a UUID identifier for the deme.
- A static IP address which is accessible by the members
- Create an email account with SMTP support through which invites are sent to the users. 

It is up to you to ensure data persistence in case the service needs to be restarted. In the future, that will be integrated into the PeaceFounder when the system will be sufficiently stable, and there will be a demand for using it. 

To run the demo, you need to start two services. One is for the peacefounder voting system, which can be started by running:

```
julia --load=peacefounder_service.jl
```

This will open the Julia shell, which shall simulate guardian interaction with the system. Look into `add_members`, `add_braid` and `add_proposal` methods to try out different scenarios. 

The second service provides means for new members to register with the deme. This, in general, is a situation that depends on how the authenticity of every member is validated. Here we shall use an email for authenticity with the `Recruiters` package. 

To start the service, we first export peacefounder recruitment parameters, printed when the `peacefounder_service.jl` is started:

```
export DEME_ROUTE='http://0.0.0.0:80'
export DEME_HASHER='sha256'
export DEME_RECRUIT_KEY='f85ccda6aab7829a114ecad6ff0357a895d'
```

Then we can start the recruiter service as:

```
julia --load=recruiter_service.jl
```

Note that you must edit the `recruiter_service.jl` and enter credentials for an email account with SMTP support for the members to receive invites to their email addresses. 

## Demo

https://www.youtube.com/watch?v=L7M0FG50ulU
