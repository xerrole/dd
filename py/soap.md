Unfortunately, at the moment, I don't think there is a "best" Python SOAP library. Each of the mainstream ones available has its own pros and cons.

Older libraries:

- **SOAPy**: Was the "best," but no longer maintained. Does not work on Python 2.5+

- **ZSI**: Very painful to use, and development is slow. Has a module called "SOAPpy", which is different than SOAPy (above).

"Newer" libraries:

- **SUDS**: Very Pythonic, and easy to create WSDL-consuming SOAP clients. Creating SOAP servers is a little bit more difficult. (This package does not work with python3.)

- **spyne**: Creating servers is easy, creating clients a little bit more challenging. Documentation is somewhat lacking.

- **ladon**: Creating servers is much like in soaplib (using a decorator). Ladon exposes more interfaces than SOAP at the same time without extra user code needed.

- **pysimplesoap**: very lightweight but useful for both client and server - includes a web2py server integration that ships with web2py.

- **SOAPpy**: Distinct from the abandoned SOAPpy that's hosted at the ZSI link above, this version was actually maintained until 2011, now it seems to be abandoned too.

- **soaplib**: Easy to use python library for writing and calling soap web services. Webservices written with soaplib are simple, lightweight, work well with other SOAP implementations, and can be deployed as WSGI applications.

- **osa**: A fast/slim easy to use SOAP python client library.

Of the above, I've only used SUDS personally, and I liked it a lot.

[Reference](https://stackoverflow.com/questions/206154/what-soap-client-libraries-exist-for-python-and-where-is-the-documentation-for)
