# DevelopmentNotification

## Installation

Point to this repo (or a fork) and bundle
```
gem 'development_notification', "0.1.0", git: 'https://github.com/CreativePublisher/development_notification', branch: 'master'
```

Run migration
```
$ rake db:migrate
```

## Configuration

```ruby
# in /config/initializers/development_notification.rb
DevelopmentNotification.configure do |config|
  config.leadersend_username = "email@example.com"
  config.leadersend_api_key = "0933e545acxc063cb8a101a374cc721f"
  config.domain = "example.com"
  config.validate! # must be called in the very end.
end
```

## Usage
After setup you gain access to:
* DevelopmentNotification::Email model that logs email prepared and sent.
* DevelopmentNotification::Email.send_email(parameter_hash) #=> sends emails

### Email sending
DevelopmentNotification::Email.send_email(title: "Systemside identifier", to: "dump@example.com", from: "creative@inbox.lv", fromname: "Creative", subject: "test", template: "html body")

## Gotchas
Engine uses smart migration inclusion, this works well in development, but production deployment that migrates selectively (like mina) may fail at detecting migrations. Be sure to __force migration__ in production. 

## Development
You need to configure the dummy app database in `spec/dummy/config/database.yml`
