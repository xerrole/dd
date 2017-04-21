# IIS

# Reading environment variables in python code

IIS run the webapp with a special virtual user, so if the app wants to access a folder, the virtual should be granted
authority to the folder.

Moreover, if webapp wants to read environment variables, the environment variables of current login user cannot be read
by webapp as webapp runs under a different sepcial virtual user. We can set environment variables in there two ways:

1. Set environment variables on system level.
2. Set environment variables in web.config.
