#Post Signup method raw json format
	http://localhost:8082/api/auth/signup
	#row details to send
	{
	    "username" : "jay",
	    "email" : "bhavsarjay@gmail.com",
	    "password" : "password",
	    "roles" : ["user","admin","moderator"]
	}

#Check public content GET
	http://localhost:8082/api/test/all


#Post Sign in content check
	http://localhost:8082/api/auth/signin
	
	#raw send
	{
    "username" : "mod",
    "password" : "password"
	}
	
	#response received
	{
	    "id": 3,
	    "username": "mod",
	    "email": "bhavsarjay01@gmail.com",
	    "roles": [
	        "ROLE_USER"
	    ],
	    "accessToken": 			"eyJhbGciOiJIUzUxMiJ9.eyJzdWIiOiJtb2QiLCJpYXQiOjE2ODAwMjA4MTYsImV4cCI6MTY4MDEwNzIxNn0.DR0FCrZRAnrpI0AUay2tnxPYbl				lPV_qGoDz1pbhifMV4QoosGHRqm1Xc_W25BO8xcKejv6Jbtt0kd4eg7O9m8w",
	    "tokenType": "Bearer"
	}