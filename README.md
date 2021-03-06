# Dwolla Ruby Gem

A Dwolla API wrapper in Ruby.

## Installation

gem install dwolla

## Resources

* View Source on GitHub (https://github.com/jeffersongirao/dwolla)
* Report Issues on GitHub (https://github.com/jeffersongirao/dwolla/issues)

## TODO

* Contacts Nearby
* Transactions Listing
* Transactions Details by ID
* Transactions Stats
* Send and Request Transactions with Other Id types (Facebook, Twitter, or Phone.)

## Usage

#### Users API

##### With Access Token 

( Auth Scope Required: accountinfofull )

```ruby
  user = Dwolla::User.me(ACCESS_TOKEN).fetch
```

##### With Client ID and Secret 

( Auth Scope Required : none )

```ruby
  client = Dwolla::Client.new(CLIENT_ID, SECRET)
  user = client.user(ACCOUNT_ID) # Dwolla account identifier or email address of the Dwolla account.
```

#### Balance API 

( Auth Scope Required : balance )

```ruby
  user = Dwolla::User.me(ACCESS_TOKEN)
  user.balance
```

#### Contacts API

##### User Contacts 

( Auth Scope Required : contacts)

```ruby
  user = Dwolla::User.me(ACCESS_TOKEN)

  # limit default is 10
  # max limit is 200

  # type default is "Dwolla"
  # valid types are "All", "Twitter", "Facebook", "LinkedIn" and "Dwolla"

  user.contacts(:search => "Bob", :type => "Dwolla", :limit => 5)
```

#### Transactions API

##### Sending Money 

( Auth Scope Required: send )

###### To a Dwolla Account

```ruby
  user = Dwolla::User.me(ACCESS_TOKEN)
  other_user_id = '812-111-1111'
  pin = '1234'
  amount = 200
	type = 'dwolla'
	description = "For that lovely dinner"

  user.send_money_to(other_user_id, amount, pin, type, description)
```

###### To an Email Address

```ruby
  user = Dwolla::User.me(ACCESS_TOKEN)
  other_user_email = 'user@example.com'
  pin = '1234'
  amount = 200
	type = 'email'
	description = "Just to say thanks"

  user.send_money_to(other_user_email, amount, pin, type, description)
```

##### Requesting Money 

( Auth Scope Required: request )

###### From a Dwolla Account

```ruby
  user = Dwolla::User.me(ACCESS_TOKEN)
  other_user_id = '812-111-1111'
  pin = '1234'
  amount = 200
	type = 'dwolla'
	description = "Gotta make rent"

  user.request_money_from(other_user_id, amount, pin, type, description)
```

###### From an email address

```ruby
  user = Dwolla::User.me(ACCESS_TOKEN)
  other_user_email = 'user@example.com'
  pin = '1234'
  amount = 200
	type = 'email'
	description = "Awesome pizza party"

  user.request_money_from(other_user_email, amount, pin, type, description)
```
