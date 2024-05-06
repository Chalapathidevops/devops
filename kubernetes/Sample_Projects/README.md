# Sample Project

## 1. MySql and WordPress Project

   **Steps to Deploy application:**
   *  Clone the yaml files 
      ```
      git clone https://github.com/Chalapathidevops/devops.git
      cd devops/kubernetes/Sample_Projects/Mysql_Wordpress/
      ```
  *  Deploy `kubectl apply -f .`
  *  Wait for the pods to be ready. `kubectl get pods`
  *  Access the wordpress frontend in a browser using the frontend's external IP.
      `kubectl get svc wordpress-service | awk {'print$4'}`
      * Fill the form and copy the password and login using the credentials
  * Backend will be stored in MqSql
      * Get the pods `kubectl get pods`
      * Login to mysql pod `kubectl exec -it mysql-647dc4b7c8-z9vmg /bin/sh` _# Here by default Mysql will be installed_
      * To login to MySql server enter the command `mysql -u root -p` and `Enter password:`  _# Enter secret password_
          ![image](https://github.com/Chalapathidevops/devops/assets/145283206/296d171c-dcf8-4a9e-a1dd-09d7a5a1ab5a)

       * Check the tables
           ```
           show databases; # Show the all the databeses
           use wordpress; # use which database want to access
           show tables; # it will show all the tables
           select * from wp_users; # Get the user information from wp_users table
           ```

           ![image](https://github.com/Chalapathidevops/devops/assets/145283206/6099a206-4cd8-4e9d-a76e-39f4d5813da5)
