We can transfer data accross different pages in multiple ways: 
- Using forms
- Pass variables using the url
- Using cookies
- Using a session
Not all of these options provide the same level of security.

In situtations where the security of the data is important, we must use sessions. PHP offers us multiple functions to work with sessions, here is non exaustive list: 
- `session_start` used to star a session
- `session_register` used to store a session variable
- `session_unregister` used to delete a session variable
- `session_is_registered` checks if a session variable has be registered for the current session.
- `session_id` returns the id of the current session
- `session_name` returns the name of the current session
- `session_unset` destroys all the variables of the current session
- `session_destroy` destroys the current session
