# Caren App: Stack, Tools, and Best Practices

This is a collection of resources, tools, and ideas meant to guide the team towards building the most stable, rock-solid production-level code base that we are capable of producing. It is likely some of these suggestions will change as we begin development in earnest and discover what works for us and what doesn't. We'll treat this is a starting point and evolve from here.

## Stack
### Backend
- #### Language: Ruby 2.5.1 ([https://www.ruby-lang.org/](https://www.ruby-lang.org/en/downloads/))
  - Recommended installation through [RVM](https://rvm.io).
- #### Framework: Rails 5.2.0 ([https://rubyonrails.org/](https://rubyonrails.org/))
  - Familiar, enables rapid development, mature with lots of  community support.
  - Should be instanciated in API mode
- #### ORM: ActiveRecord ([http://guides.rubyonrails.org/](http://guides.rubyonrails.org/active_record_basics.html)) 
  - Default ORM for Rails 
- #### Database: PostgreSQL 10.4 ([https://www.postgresql.org/](https://www.postgresql.org/))
  - Familiar, relational, plays nicely with ActiveRecord and GraphQL
  - Adopted by major Rails hosting providers.
  - Use for Development, Staging, and Production (but not Testing) environments.
- #### GraphQL Ruby Server Library ([https://graphql.org/](https://graphql.org/code/#ruby))
  - Provides a versionless API, no need for extensive API documentation, and makes for single, inexpensive queries from the front end.
- #### Build Tools: Bundler ([https://bundler.io/](https://bundler.io/))
  - Default package management for Rails

### Frontend
- #### Language: ES6 ([http://es6-features.org/](http://es6-features.org/))
  - The native language of React Native (React Native ships with the Babel JavaScript compiler anyway). Definitely a step up from core ES5 in terms of syntax and available features.
- 
- #### Framework: React Native ([https://facebook.github.io/react-native/](https://facebook.github.io/react-native/))
  - Used by major players to developer AAA apps.
  - Allows for a lot of code reuse across iOS and Android platforms.
- #### Static Type Checking: Flow ([https://flow.org/](https://flow.org/))
  - Adds type checking to ES6 at compile time. Among other advantages, this allows for earlier detection of bugs and errors and gives the code more readability. [Here](https://medium.freecodecamp.org/why-use-static-types-in-javascript-part-2-part-3-be699ee7be60) is a good article about the pros and cons of static type checking.
- #### GraphQL - Apollo or Relay Modern ([https://graphql.org](https://graphql.org/code/#javascript-1))
  - Suggesting Apollo over Relay Modern due an easier learning curve and the fact that it is built on top of redux. Although Apollo and Relay are capable of producing the same results, the benefit of Relay Modern is an opinionated approach to organization and structure as well. This highly opinionated approach allows Redux to be dropped from the stack.  

- #### Experimentation: Expo ([https://expo.io/](https://expo.io/))
  - Note: This is useful for experimentation and (potentially) prototyping only. The expo app is essentially a wrapper around one's own app, locking it into an ecosystem and preventing the use of specific packages that use native hooks. Debugging and connection wih a device or simulator can also be troublesome (in my personal experience). Use of pure react native is recommended. 

- #### Pure React Native: Android Studio / Xcode ([Building Projects with Native Code](https://facebook.github.io/react-native/docs/getting-started.html))
  - It should be noted that 'Native Code' does not refer to Java or Swift but to 'Pure React Native'. It is still JavaScript.
  - Scaffolding to get individual Android and iOS projects up and running.
  - Provides device simulators for development as well as tools to test on real devices.

- #### Build Tools: [Node](https://nodejs.org/en/) and [NPM](https://www.npmjs.com/)
  - Stick with node and npm for simplicity sake unless we decide we need something more robust.
  - [Features of popular package managers](https://stackoverflow.com/questions/35062852/npm-vs-bower-vs-browserify-vs-gulp-vs-grunt-vs-webpack)
  - [User feedback for popular package managers](https://stackoverflow.com/questions/35062852/npm-vs-bower-vs-browserify-vs-gulp-vs-grunt-vs-webpack)


## Testing
### Backend
- #### BDD 101 ([https://automationpanda.com/](https://automationpanda.com/2017/01/25/bdd-101-introducing-bdd/))
  - A series of articles detailing best practices for Behaviour Driven Development (TDD done correctly).
- #### Database: SQLite ([https://www.sqlite.org](https://www.sqlite.org/index.html))
  - In memory database that can be used to speed up automated tests.  
- #### Tools for Rails Unit and API Integration Tests
  - [Rspec](http://rspec.info)
  - [Factory Bot](https://github.com/thoughtbot/factory_bot)
  - [Faker](https://github.com/stympy/faker)
  - [Shoulda Matchers](https://github.com/thoughtbot/shoulda-matchers)
  - [Database Cleaner](https://github.com/DatabaseCleaner/database_cleaner)
- #### Helpful Resources
  - [Effective Testing With Rspec (book)](https://pragprog.com/book/rspec3/effective-testing-with-rspec-3)
  - [Rails API integration tests](https://lnikki.la/articles/rails-api-integration-tests-1/)
  - [Rails API testing guidelines](http://matthewlehner.net/rails-api-testing-guidelines/)
  - [Rspec JSON API testing](https://blog.eq8.eu/article/rspec-json-api-testing.html) 
  - [Rspec RAILS API controller tests](http://www.thegreatcodeadventure.com/better-rails-5-api-controller-tests-with-rspec-shared-examples/)
  - [Pluralsight Courses](https://app.pluralsight.com/library/search?q=rspec)
    - Note: a free, 3 month subscription to pluralsight is available through Microsoft/Visual Studio [here](https://docs.microsoft.com/en-us/visualstudio/subscriptions/vs-pluralsight).

### Frontend
  - #### Tools for React Native Unit, Integration, and End to End Testing
    - [Jest](https://facebook.github.io/jest/)
    - [Travis](https://docs.travis-ci.com/)
    - [Calabash](https://calaba.sh/) (Mobile UI testing)
      - There exist a few alternatives to this that may be worth exploring, namely [Cavy](https://github.com/pixielabs/cavy) and [Detox](https://github.com/wix/detox). Detox looks like the best of the bunch but, unfortunately, it only availble for iOS at the moment. Android is on its way, however.


## Security
- #### User Authentication
  - #### [Amazon Cognito](https://aws.amazon.com/cognito/) + [AWS Amplify](https://github.com/aws/aws-amplify)
    - allows for two factor phone authentication
    - allows for users to sign up with email but leverages amazons security
    - allows for social login
    - uses JSON Web Tokens to authorize requests to our Rails / GraphQL API
  - #### Helpful Resources
    - [Decoding AWS Cognito JWT tokens in Rails](https://medium.com/@victor.leong.17/decoding-aws-cognito-jwt-in-rails-f88c1c4db9ec)
    - [Production tested React Native Authentication](https://medium.com/react-native-training/react-native-authentication-in-depth-8d8c2e4ad81b)   
- #### Ruby
  - [Ruby security documentation](http://ruby-doc.org/core-2.2.3/doc/security_rdoc.html)
  - [Up to date database of insecure gems](https://github.com/rubysec/ruby-advisory-db/)
  -  [List of known Ruby vulnerabilities](https://www.cvedetails.com/product/12215/Ruby-lang-Ruby.html?vendor_id=7252)
- #### Rails
  - [Rails Security Checklist](https://github.com/brunofacca/zen-rails-security-checklist)
  - [Preproduction Checklist](https://blog.codeship.com/preproduction-checklist-for-a-rails-app/)
  -  [Open Web Application Security Project - Rails](https://www.owasp.org/index.php/Ruby_on_Rails_Cheatsheet)
- #### Database Encrytion
  - Message Encryptor
  - attr_encrypted
- #### AWS
  - [McAfee's List of 51 Best Practices](https://info.skyhighnetworks.com/rs/274-AUP-214/images/WP-Definitive-Guide-to-AWS-eBook.pdf) 


- #### Network
  - Use HTTPS and SSL certificates to provde encryption and prevent packet sniffing on an unsecured network.
- #### React Native
  - [SSL Pinning](https://possiblemobile.com/2013/03/ssl-pinning-for-increased-app-security/) to prevent additional MitM attacks.
    - checking the server’s certificate against a known copy of that certificate. This is done by bundling the server’s SSL certificate inside the client-side application, making sure any SSL request first validates the server’s certificate against the bundled certificate.
    - not to be confused with [Public Key Pinning](https://www.theregister.co.uk/2017/10/30/google_hpkp/) which Google championed for a few years before realizing it caused more problems than it was worth.
  - Validation
      - Just a quick reminder that frontend validation is for UX only and not meant for security. All input validation should also be done on the back end.   

## Performance and Optimization

  - http://guides.rubyonrails.org/v3.2.13/performance_testing.html
  - https://robots.thoughtbot.com/how-to-evaluate-your-rails-json-api-for-performance-improvements
  - [Free Cloud Based Load Tester](https://loader.io/)

## Error and Exception Handling

## Documentation

## Version Control
- Git
- Github
  - Thoughts: Single Repo vs Multiple Repos vs SubRepos 

- - Workflow: http://dontpanic.42.nl/2014/10/the-case-for-separating-front-and-back.html

change master's name to 'production' (should always be delopyable).
github flow

https://www.youtube.com/watch?v=juLIxo42A_s

## DevOps
- Amazon Elastic Bean Stalk

## Architecture
We will likely start with the Monolithic approach for the MVP and adopt a Modular approach (using engines) in the future.
Chat feature will likely be treated as a microservice and not even be written in rails.
  - [The Modular Monolith](https://medium.com/@dan_manges/the-modular-monolith-rails-architecture-fb1023826fc4)
  - [Rails Engines Guide](http://guides.rubyonrails.org/engines.html)
  - [Modular Rails PDF](https://www.evernote.com/shard/s297/res/e8503aae-74dc-4cb2-890a-dfb9826a2664/modular_rails.pdf?search=modular%20rails)



## Style Guides

### Javascript
  - [JavaScript Standard Style ](https://github.com/standard/standard)

### Ruby
  - [Ruby Style Guide](https://github.com/bbatsov/ruby-style-guide)
  - https://github.com/bbatsov/rubocop

### Git
  - [Semantic versioning](https://semver.org/)
  - [Writing a good commit message](https://chris.beams.io/posts/git-commit/)
  - [Auto commit message validation - ruby](https://github.com/m1foley/fit-commit)
  - [Auto commit message validation - node](https://github.com/clns/node-commit-msg)

### Further Resources
  - [Ruby on Rails - Notes for Professionals](https://goalkicker.com/RubyOnRailsBook/)


