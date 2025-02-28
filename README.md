# spring-security

- Http request
- **Security Filter Chain** -> Responsible for performing security checks based on the configuration we have, If any of the condition is not met then we might get 401 or 403 error.
- **JWTAuthenticationFilter** -> It's job is to intercept the request and check if the token is sent to the server. It creates the UsernamePasswordAuthenticationToken which is then used to perform the authentication.
- **AuthenticationManager** -> The object (interface) which is responsible for performing the authentication. It is an API that defines how spring security filters perform authentication. It takes the request and tries to authenticate the user based on the AuthenticationProvider.
    - **ProviderManager** -> It is the most commonly used implementation of the AuthenticationManager. It is responsible for picking a provider like DaoAuthenticationProvider, JWTAuthenticationProvider etc.
    - **DaoAuthenticationProvider** -> It does authentication based on the username and password, and it requires the PasswordEncoder to make sure that when it gets the hashed password from the database whether the two password matches, not the content but the actual hash.
    - **UserDetailsService** -> This pretty much loads the user from the database.
    - **UserDetails** -> The user has to implement the UserDetails. 
- **SecurityContextHolder** -> If the authentication succeds, this will holds the information of the current authenticated user. If the authentication fails we want to remove the user from the SecurityContextHolder and if the authentication succeds we want to add the user to the SecurityContextHolder.
