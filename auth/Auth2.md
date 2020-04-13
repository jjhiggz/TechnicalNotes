Verify user identities in rails
  
  1. Create a login Route
   

  GO into  your routes file and add a '/login' rout that connects to an authentication controller and want it to got o its login action 

    ```
    Rails.application.routes.draw do
      
      resources :users, only: [:create]
      post "/login", to: "authentication#login"

    end

    ```

  2. Create a login controller/action
  
  Go into the Authentication Controller and create an action called login

  3. look up a user
    
    class AuthenticationController < ApplicationController
    
      @user = User.find_by username: params[:username]

      if !@user
        render json: { message: "User Not Found"}
      else
        if @user.authenticate(params[:password])
          render json: {message: "Correct"}
        else
          render json: {message: "Wrong Password"}
        end
      end
    end

    
  4. Authenticate Them
  5. 
  6. Create a Token
    
  first you need to add a gem to your folder called jwt

    bundle add jwt
  
    you have to require 'jwt' in there as well



  Then you add a token into your authentication controller
     class AuthenticationController < ApplicationController
    
      @user = User.find_by username: params[:username]

        if!@user or !@user.authenticate params[:password}
          render json: { message: "Wrong something!"}
        else
          payload = {
            user_id: @user.id,
            message: " Hi mom"
            username: @user.username,
          }
          secret_key = Rails.application.secret_key_base
          token = JMT.encode(payload, secret_key)

          render json: {token: token}

      end



  1. Sign it 
  2. Send it
  3. 

Issue signed tokens to users

Differentiate between authorization and authentication







const loginBody = {
    user: { 
      username,
       password
       }
}

const loginFormData = new FormData(event.target)
const username = loginFormData.get("username")
const username = loginFormData.get("password")

fetch ("http://localhost:3000/login" , {
  Method "POST",
  headers: {
      "contentType":"application/json"
  }

}
event.preventDefault();
event.target.reset();