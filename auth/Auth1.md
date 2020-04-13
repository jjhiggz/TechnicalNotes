Steps to Auth
1) Uncomment Bcrypt
2) Run Install
3) Have a Create Rout

``` 
class UsersController < Applicationcontrollere
  def create
    @user = User.create({
      username:params[:username],
      password: params[:password],
      display_name: params[:display_name]
    })

    render json: {user: @user}, status: : created
  end
end

```

Inside of the model
```
class User < ApplicationRecord
  has_secure_password
end
```

Inside of the migration
```
def change
  create_table :users do|t|
    t.string :username
    t.string :display_name
    t.string :password_digest
    t.timestamps
  end
end
```
A password digest is an example of a hash


Options for rails are bcrypt and md5 and 


The difference betweren encoding, encrypting, and hashing is as follows

Encoding is liek changing a language, and you can do it in both directions

Hashing is a math thing. For example CAT turns into 3 1 20 - >  3+1+20 turns to 24 turns to 6 and then you can check that number. It only works one way but not the other

encryption is a bit different
it is much easier to calculate one way then the other. Its always mathematically more difficult to go one way than the other

frequency attack
  If you use a really common password, you can start to guess what passwords are. So like iff 500 people have the password that is password you can go back from the hashs


An salt is when the encrypt thang, you add random characters to the end of the password. Those letters are called the salt. And then when you combine the hash it completely changes the number


