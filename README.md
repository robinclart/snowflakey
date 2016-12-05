# Snowflakey

Unique ID generator.

## Generation

You can generate a simple snowflake by calling `#generate` without
any arguments.

```ruby
Snowflakey.generate # => "567wz82coauesrlb522"
```

You can also pass a prefix that will be prepended to the snowflake.

```ruby
Snowflakey.generate("snow") # => "snow_567wz9ox8b8p58tngzu"
```

Finally it also works with multiple prefixes.

```ruby
Snowflakey.generate(["snow", "flake"]) # => "snow_flake_567wz6ecywb6d6ruor9"
```

You can also change the size of the snowflake.

```ruby
Snowflakey.generate("snow", size: 64) # => "snow_2mdov6imct3o4"
```

You can also use another base.

```ruby
Snowflakey.generate("snow", base: 16) # => "snow_ac6591aa22063660af0e05d4"
```

## Verification

```ruby
snowflake = Snowflakey.verify("snow_567z7pfvdq47fswkt52")
```

This will return the snowflake as if it had been created with the low level API.
You can then fetch the size, the time, the ID, the base, etc.

Note that if the snowflake was created with another base than 36 and with another size than 96 you will have to declare those when calling `#verify`.

## Manual Initialization

If you need you can also initialize a snowflake without using the `#generate` method. This gives you more control over every parameters.

```ruby
prefix = "snow"
size   = 96
time   = Time.parse("2016-12-04T22:22:22Z").utc
id     = 3104654282887302
base   = 36

snowflake = Snowflakey::Snowflake.new(prefix, size, time, id, base)
```

You can then call `#to_s` to get the snowflake as a string.

```ruby
snowflake.to_s # => "snow_567z7pfvdq47fswkt52"
```

## Important Remark

> You are not special. You're not a beautiful and unique snowflake. You're the same decaying organic matter as everything else. We're all part of the same compost heap. We're all singing, all dancing crap of the world.
