What is Serialization?

Serialization is basically the formatting of data in a consistent way. 

For example take the following hash in ruby
```
data = {
  username: "jjhiggz",
  name: "Jonathan Higger",
  age "nonya"
}
```
perhaps it would be useful to format this in a standard way such as 

```
data = {
  user: {
      username: "jjhiggz",
      name: "Jonathan Higger",
      age "nonya"
    },
}
```
this is what serialization is


in order to do this type of thing we can use the following command in ruby

```
rails g serializer users
```

then in your controller instead of rendering you're raw data to Json you can just render the serialized data to JSON

inside of the attributes on the serializer you can add the attributes that you want to add
```
:name, :age, ect...
```
