# dual-boot-rails
A sample project to verify dual booting a rails app.

It supports running application in next version as well as current version

To run the application: 
For running the current version (ex : version 3.2.2)
```
RAILS_NEXT=0 bundle install
RAILS_NEXT=0 Rails server
```

For running the next version (ex : version 4.2.0)
```
RAILS_NEXT=1 bundle install
RAILS_NEXT=1 Rails server
```
T.B.D
--Validating support for custom gems
--Creating a script enable smooth running of different versions.
