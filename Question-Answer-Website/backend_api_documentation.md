# API Documentation

#### TODO:

1. Make the structure for Static text JSON, which includes:
	- homepage_div
	- class_div
	- contact_div
	- city_id list

Eg:

```
{
    "homepage":{
        "prominent_message": "Your kids personal brain trainer"
    }
    "contact_div":{
        "contact_info":{
            "title_message": "Contact-Info",
            "adress": "CampusConnect Technologies Private limited, 105 A Wing 1st floor, Kanara Business Center, Sawali Society, Laxmi Nagar, Ghatkopar East, Mumbai –400075",
            "phone"
        }
        "query_box":{
            
        }
    }                
}
```

### Aim:
This document aims to provide a general understanding of the backend APIs and its details.

### Definitions:

#### 1. Response: 
##### 1.1. Meta-Data-Response:
A response is called Meta-Data-Response when it satisfies the following JSON schema
```
{
	"meta" : "This is used to provide any meta information about the API, mostly not used by clients (browsers/apps)",
	"data" : { 
				"data_key":"data value" 
			 }
}
```

##### 1.2. HTTP_200_OK
A __Meta-Data-Response__ to represent the Successfull API call
Status: __200__
Generic __200__ JSON:
```
{
	"meta":"",
	"data":{

	}	
}
```

##### 1.3. HTTP_400_BAD_REQUEST
A __Meta-Data-Response__ to represent the response where client call the API with incorrect request.
Status: __400__
Generic __400__ JSON:
```
{
  "meta": "",
  "data": {
    "error_message": "This is an example message: The Email Id you are using is already registered with us. Kindly use a different one",
    "error_data": {}
  }
}
```
##### 1.4. HTTP_403_FORBIDDEN
A __Meta-Data-Response__ to represent the response where client tries to access the resource which it doesnt have the acess.
Status: __403__
Generic __403__ JSON:
```
{
  "meta": "",
  "data": {
    "error_message": "This is an example message: You are not allowed to view this!",
    "error_data": {}
  }
}
```
##### 1.5. HTTP_404_NOT_FOUND
A __Meta-Data-Response__ to represent the response where client tries to access the resource which does not exist.
Status: __404__
Generic __404__ JSON:
```
{
  "meta": "",
  "data": {
    "error_message": "This is an example message: The User Id:123 doesnt not exists",
    "error_data": {}
  }
}
```
##### 1.6. HTTP_500_INTERNAL_SERVER_ERROR __500__
A __Meta-Data-Response__ to represent the response where code fails at the server end.
Status: __500__
Generic __500__ JSON:
```
{} 
```
##### 1.7. ALL_GENERIC_STATUS_RESPONSE_FORMAT
__ALL_GENERIC_STATUS_RESPONSE_FORMAT__ implies that the given API satisfies the following:
* Gives __HTTP_200_OK__ Response for 200
* Gives __HTTP_400_BAD_REQUEST__ Response for 400
* Gives __HTTP_403_FORBIDDEN__ Response for 403
* Gives __HTTP_404_NOT_FOUND__ Response for 404
* Gives __HTTP_500_INTERNAL_SERVER_ERROR__ Response for 500

##### 1.8. EXCEPTIONED_GENERIC_STATUS_RESPONSE_FORMAT
__ALL_GENERIC_STATUS_RESPONSE_FORMAT__ implies that the given API satisfies the following:
* Gives __HTTP_200_OK__ Response for 200
* Gives __HTTP_400_BAD_REQUEST__ Response for 400
* Gives __HTTP_403_FORBIDDEN__ Response for 403
* Gives __HTTP_404_NOT_FOUND__ Response for 404
* Gives __HTTP_500_INTERNAL_SERVER_ERROR__ Response for 500
* In case the API overrides the above condition its stated below

#### 2. Response: 
##### 2.1. LoggedIn-Header:

A header is defined as LoggedIn-Header when the header has the session token in it. This type of header is used for the user who is the registered user and has logged into the system.

LoggedIn-Header JSON:
```
{
	"session_token":"logiqid_34_mYrmAIJA6TUDqfOvpfqez7fM9Mp11n2b"
}
``` 

The session_token value follows the given pattern:
```
logiqid_<customer_id>_<uuid>
```
where **uuid** is a 32 Character unique text used for user identification

##### 2.2. Platform-Header:

A header is defined as Platform-Header when the header has the information about the platform which is calling the API. This type of header is used for the cases when the same API needs to served differently for different Platforms.
 
Platform-Header JSON:
```
{
	"source":"desktop_browser"
}
```

source can take any of the following values:
-   web: When the API is called from Desktop browser
-   mweb: When the API is called from Mobile browser
-   android: When the API is called from Android App
-   ios: When the API is called from IOS App
  
In our system we will be having either:

Loggedin-Platform-Header = Loggedin-Header + Platform-Header
```
{
	"session_token":"logiqid_34_mYrmAIJA6TUDqfOvpfqez7fM9Mp11n2b",
	"source":"desktop_browser"
}
```

Platform-Header
```
{
	"source":"desktop_browser"
}
```

#### 3. Versioning:
We will be utilising the URL based Versioning i.e we will use the version number in the URL.

### Documentation

#### PreLogin APIs

1.	
	- API Name: Reviews API
	- URL: /products/review/
	- Method: GET
	- Header: Platform-Header
	- Request: No Query Params
	- Response: __ALL_GENERIC_STATUS_RESPONSE_FORMAT__
> __HTTP/1.1 200 OK__
```
{
    "meta":"",
    "data":[
        {
            "review_url":"https://www.fb.com/comment/123",
            "image_url":"https://www.facebook.com/img/123",
            "review":"Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmo tempor incididunt utnsequat",
            "reviewer":"Rita Singh"
        },
        {
            "review_url":"https://www.fb.com/comment/123",
            "image_url":"https://www.facebook.com/img/123",
            "review":"Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmo tempor incididunt utnsequat",
            "reviewer":"Rita Singh"
        }
    ]
}
```
2.
	- API Name: School Partnership API
	- Status: Might not be required, need to be discussed
	- URL: /products/school_partnership/
	- Method: GET
	- Header: Platform-Header
	- Request: No Query Params
	- Response: __ALL_GENERIC_STATUS_RESPONSE_FORMAT__
> __HTTP/1.1 200 OK__
```
{
  "meta": "",
  "data": [
	  {
	    "image_url": "https://www.facebook.com/img/123",
	    "school": "Kendriya Vidhyalaya 1",
	    "info": ""
	  },
	  {
	    "image_url": "https://www.facebook.com/img/123",
	    "school": "Kendriya Vidhyalaya 1",
	    "info": ""
	  },
	  {
	    "image_url": "https://www.facebook.com/img/123",
	    "school": "Kendriya Vidhyalaya 1",
	    "info": ""
	  },
	  {
	    "image_url": "https://www.facebook.com/img/123",
	    "school": "Kendriya Vidhyalaya 1",
	    "info": ""
	  },
	  {
	    "image_url": "https://www.facebook.com/img/123",
	    "school": "Kendriya Vidhyalaya 1",
	    "info": ""
	  }
  ]
}
```

3.
	- API Name: Contact Us Post API
	- Status: Need to be discuss the URL
	- URL: /company/contact/
	- Method: POST
	- Header: Platform-Header
	- Request: __ALL_GENERIC_STATUS_RESPONSE_FORMAT__
```
{
    "name" : "Nimesh Verma",
    "email" : "nimesh.aug11@gmail.com",
    "mobile" : "9911616971",
    "city":"Mumbai",
    "query : "Can I get test package for my 9 month baby?",
    "captcha_valid" : true,
  }
}
```
	- Response: __ALL_GENERIC_STATUS_RESPONSE_FORMAT__
> __HTTP/1.1 200 OK__
```
{
    "meta" : "",
    "data" : {
        "message":"Your query has been submitted, We will get back to you ASAP"
  }
}
```

4. #CHECK: Do we still need this
	- API Name: Captcha API
	- Status: Need to be discuss the Usage and URL
	- URL: /utility/captcha/
	- Method: GET
	- Header: Platform-Header
	- Request: No Query Params
	- Response: __ALL_GENERIC_STATUS_RESPONSE_FORMAT__
> __HTTP/1.1 200 OK__
```
{
  "meta": "",
  "data": {
    "image_url": "https://www.facebook.com/img/123",
    "correct_value": "IVijqer"
  }
}
``` 

5.	- API Name: Pricing API
	- Status: Need to be discuss the Usage and URL
	- URL: /product/pricing/
	- Method: GET
	- Header: Platform-Header
	- Request: No Query Params
	- Remark: The content package data and the test package data can take every combination in the content + test case so we shouldn't send the package data again in the content + test case. The discount on the content + test case can be passed in the content + test column as a percentage amount and the front end can contain the logic to round of the figure so that the customer doesn't see prices in floating points.
	- Response: __ALL_GENERIC_STATUS_RESPONSE_FORMAT__
> __HTTP/1.1 200 OK__ 

```
{
	"meta": "",
	"data": {
		"message": {
			"heading": "Simple & transparent pricing",
			"bottom": "15-Days, No Questions Asked, Full Money-Back uarantee. (Valid only for he Content Subscription)"
		},
		"pricing": {
			"test": {
				"image_url": "https://www.facebook.com/img/123",
				"name": "Test",
				"description": "Includes 4 sample papers and 5 Topic Notes",
				"price": 550,
				"offer": {
					"price": 450,
					"validity_date": "21/7/2017",
					"text": "Early bird discount till"
				},
				"button_text": "Buy Now",
				"features": [{
						"image_url": "https://www.facebook.com/img/123",
						"status": true,
						"text": "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incidid"
					},
					{
						"image_url": "https://www.facebook.com/img/123",
						"status": true,
						"text": "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incidid"
					},
					{
						"image_url": "https://www.facebook.com/img/123",
						"status": true,
						"text": "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incidid"
					},
					{
						"image_url": "https://www.facebook.com/img/123",
						"status": true,
						"text": "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incidid"
					}
				]
			},
			"content": {
				"image_url": "https://www.facebook.com/img/123",
				"name": "Content",
				"description": "dcdsc svfv",
				"price": [{
						"period": "3 months",
						"price": 900,
						"package_id": 12
					},
					{
						"period": "6 months",
						"price": 1400,
						"package_id": 12
					},
					{
						"period": "1 year",
						"price": 2200,
						"package_id": 12
					}
				],
				"button_tex": "Buy Now",
				"city_id_list": [

				],
				"features": [{
						"image_url": "https://www.facebook.com/img/123",
						"status": true,
						"text": "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incidid"
					},
					{
						"image_url": "https://www.facebook.com/img/123",
						"status": true,
						"text": "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incidid"
					},
					{
						"image_url": "https://www.facebook.com/img/123",
						"status": true,
						"text": "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incidid"
					},
					{
						"image_url": "https://www.facebook.com/img/123",
						"status": true,
						"text": "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incidid"
					}
				]
			},
			"test_and_content": {
				"image_url": "https://www.facebook.com/img/123",
				"name": "Content and Test",
				"description": "ddwwdwdsa edewsds ",
				"discount": { 
						"percentage": 10,
						"validity_date": "21/7/2017",
						"text": "10% Off",
				},
				"button_tex": "Buy Now",
				"features": [{
					"image_url": "https://www.facebook.com/img/123",
					"status": true,
					"text": "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incidid"
				}]
			}
		}
	}
}
```

6.  
	- API Name: City API
	- Status: Need to be discuss URL
	- URL: /utility/test/city/
	- Method: GET
	- Header: Platform-Header
	- Request: No Query Params
	- Response: __ALL_GENERIC_STATUS_RESPONSE_FORMAT__
> __HTTP/1.1 200 OK__
```
{
  "meta": "",
  "data": [
  {
    "id": 1,
    "name": "Mumbai",
    "supported": true
  },
  {
    "id": 2,
    "name": "Pune",
    "supported": true
  },
  {
    "id": 3,
    "name": "Ahemdabad",
    "supported": true
  },
  {
    "id": 4,
    "name": "Nasik",
    "supported": true
  },
  {
    "id": 5,
    "name": "Bhopal",
    "supported": false
  },
  {
    "id": 6,
    "name": "Other",
    "supported": true
  }
  ]
}
```


7.        
	- API Name: Class API
	- Status: Need to be discuss URL
	- URL: /user/class/
	- Method: GET
	- Header: Platform-Header
	- Request: No Query Params
	- Response: __ALL_GENERIC_STATUS_RESPONSE_FORMAT__
> __HTTP/1.1 200 OK__
```
{
  "meta": "",
  "data": [
  {
    "id": 1,
    "name": "Sr KG",
    "supported": true
  },
  {
    "id": 2,
    "name": "Class 1",
    "supported": true
  },
  {
    "id": 3,
    "name": "Class 2",
    "supported": true
  },
  {
    "id": 4,
    "name": "Class 3",
    "supported": true
  },
  {
    "id": 5,
    "name": "Class 4",
    "supported": false
  },
  {
    "id": 6,
    "name": "Class 5",
    "supported": true
  },
  {
    "id": 7,
    "name": "Class 6",
    "supported": true
  },
  {
    "id": 8,
    "name": "Class 7",
    "supported": true
  },
  {
    "id": 9,
    "name": "Class 8",
    "supported": true
  },
  {
    "id": 10,
    "name": "Class 9",
    "supported": true
  }
  ]
}
```

8.	- API Name: Test Info API
	- Status: Need to be discuss URL
	- URL: /test/info/
	- Method: GET
	- Header: Platform-Header
	- Request: {}
	- Response: __ALL_GENERIC_STATUS_RESPONSE_FORMAT__
> __HTTP/1.1 200 OK__
```
{
  "meta": "",
  "data": {
    "city_data": [
      {
        "city_id": 1,
        "city_name": "Mumbai",
        "price":550,
        "package_id": 1,
        "test_schedule": [
          {
            "name": "Level 1:",
            "image_url": "https://www.facebook.com/img/123",
            "schedule": "October 29",
            "venue": "Khar Education Society (Khar) & DD Rashtriya Shala (Ghatkopar)"
          },
          {
            "name": "Level 2:",
            "image_url": "https://www.facebook.com/img/123",
            "schedule": "November 12",
            "venue": "Gopi Birla Memorial School(Walkeshwar) & PPS Kandivali (Kandivali) & C P Goenka International School, Thane"
          }
        ]
      },
      {
        "city_id": 1,
        "city_name": "Mumbai",
        "price":550,
        "package_id": 1,
        "test_schedule": [
          {
            "name": "Level 1:",
            "image_url": "https://www.facebook.com/img/123",
            "schedule": "October 29",
            "venue": "Khar Education Society (Khar) & DD Rashtriya Shala (Ghatkopar)"
          },
          {
            "name": "Level 2:",
            "image_url": "https://www.facebook.com/img/123",
            "schedule": "November 12",
            "venue": "Gopi Birla Memorial School(Walkeshwar) & PPS Kandivali (Kandivali) & C P Goenka International School, Thane"
          }
        ]
      }
    ]
  }
}
```

9.	- API Name: Registration API
	- Status: Need to discuss URL
	- URL: /user/registration/
	- Method: POST
	- Header: Platform-Header
	- Request:
``` 
{
  "full_name": "Nimesh Kiran Verma",
  "mobile_number":"9911616971",
  "email":"nimesh.aug11@gmail.com",
  "city_id":1,
  "class_id":1,
  "school":"St Xaviers Sr Sec School",
  "password":"password123"
  "refer_code":"Mikin7332"
}
```
	- Response: __EXCEPTIONED_GENERIC_STATUS_RESPONSE_FORMAT__
> __HTTP/1.1 200 OK__
```
{
  "meta": "",
  "data": {
    "customer_id": 101,
    "session_id": "logikids_101_Ad10w9TSOLRlH0tI6clnA8KXchFXd3kl"
  }
}
```
> __HTTP/1.1 404 Not Found__: Use Generic Response
> __HTTP/1.1 400 Bad Request__: 
If the email input is not a valid email  
```
{
	"meta":"",
	"data":{
		"error_message": "The email is not a valid email"
	}
}
```
If a user with that email already exists  
```
{
	"meta":"",
	"data":{
		"error_message": "A user with this email already exists"
	}
}
```
If the mobile number is not a valid 10 digit number  
```
{
	"meta":"",
	"data":{
		"error_message": "The mobile number is not a valid 10 digit number"
	}
}
```
If the city id does not exist  
```
{
	"meta":"",
	"data":{
		"error_message": "This city_id does not exist"
	}
}
```
If the school name is invalid  
```
{
	"meta":"",
	"data":{
		"error_message": "school name is not present in our system"
	}
}
```
If the school name is valid but present in the city specified by the city_id  
```
{
	"meta":"",
	"data":{
		"error_message": "There is no such school name in the city you have selected"
	}
}
```
If the refer code is invalid  
```
{
	"meta":"",
	"data":{
		"error_message": "The refer code is invalid"
	}
}
```

10.
	- API Name: Test Leads API
	- Status: Need to be discuss URL
	- URL: /user/lead/
	- Method: POST
	- Header: Platform-Header
	- Request:
``` 
{
  "full_name": "Nimesh Kiran Verma",
  "mobile_number": "9911616971",
  "email": "nimesh.aug11@gmail.com",
  "city_id": 1,
  "class_id": 1,
  "school": "St Xaviers Sr Sec School",
}
``` 
	- Response: __EXCEPTIONED_GENERIC_STATUS_RESPONSE_FORMAT__
> __HTTP/1.1 200 OK__
```
{
  "meta": "",
  "data": {
    "sample_test_paper": "Multipart PDF File",
    "message": "Thanks for trying Us"
}
```
> __HTTP/1.1 404 Not Found__: Use Generic Response
> __HTTP/1.1 400 Bad Request__: 
>> #NOTE: These error cases need to be discussed separately as most of these can be handled in the font-end
If the email input is not a valid email  
```
{
	"meta":"",
	"data":{
		"error_message": "The email is not a valid email"
	}
}
```
If a user with that email already exists  
```
{
	"meta":"",
	"data":{
		"error_message": "A user with this email already exists"
	}
}
```
If the mobile number is not a valid 10 digit number  
```
{
	"meta":"",
	"data":{
		"error_message": "The mobile number is not a valid 10 digit number"
	}
}
```
If the city id does not exist  
```
{
	"meta":"",
	"data":{
		"error_message": "This city_id does not exist"
	}
}
```
If the school name is invalid  
```
{
	"meta":"",
	"data":{
		"error_message": "school name is not present in our system"
	}
}
```
If the school name is valid but present in the city specified by the city_id  
```
{
	"meta":"",
	"data":{
		"error_message": "There is no such school name in the city you have selected"
	}
}
```

11.
	- API Name: Login API
	- Status: Need to be discuss URL
	- URL: /user/login/
	- Method: POST
	- Header: Platform-Header
	- Request:
```
{
  "email":"nimesh.aug11@gmail.com",
  "password":"password123"
}
``` 
	- Response: __EXCEPTIONED_GENERIC_STATUS_RESPONSE_FORMAT__
> __HTTP/1.1 200 OK__ 
```
{
  "meta": "",
  "data": {
    "customer_id": 101,
    "session_id": "logikids_101_Ad10w9TSOLRlH0tI6clnA8KXchFXd3kl"
  }
}
```
> __HTTP/1.1 404 Not Found__: Use Generic Response
> __HTTP/1.1 400 Bad Request__: 
If the user credentials are not correct  
```
{
	"meta":"",
	"data":{
		"error_message": "The email or password entered are not correct"
	}
}
```

12.
	- API Name: Forgot Password API
	- Status: Need to be discuss URL
	- URL: /user/forgot_password/
	- Method: POST
	- Header: Platform-Header
	- Request: 
```
{
  "email":"nimesh.aug11@gmail.com",
}
``` 
	- Response: __EXCEPTIONED_GENERIC_STATUS_RESPONSE_FORMAT__
> __HTTP/1.1 200 OK__
```
{
  "meta": "",
  "data": {
  "message ":"Password Reset Link has been sent to your registered Email"
  }
}
```
> __HTTP/1.1 404 Not Found__: Use Generic Response
> __HTTP/1.1 400 Bad Request__: 
If the email is not associated with any user in our database  
```
{
	"meta":"",
	"data":{
		"error_message": "This email is not associated with any user in our database"
	}
}
```

13.1
	- API Name: Reset Password API
	- Status: Need to be discuss URL
	- URL: /user/forgot_password_link/
	- Method: GET
	- Header: Platform-Header
	- Request: Query Params
id=4675&code=uAm-wlA6HKsuZsZYREZlgfkJzhR7ikG3 
	- Response: __EXCEPTIONED_GENERIC_STATUS_RESPONSE_FORMAT__
> __HTTP/1.1 200 OK__
```
{
  "meta": "",
  "data": {
	  "email": "nimesh.aug11@gmail.com"
  }
}
```
> __HTTP/1.1 404 Not Found__: Use Generic Response

13.2
	- API Name: Reset Password API
	- Status: Need to be discuss URL
	- URL: /user/forgot_password_link/
	- Method: POST
	- Header: Platform-Header
	- Request:
```
{
  "id": "4675",
  "code": "uAm-wlA6HKsuZsZYREZlgfkJzhR7ikG3",
  "email ":nimesh.aug11@gmail.com,
  "password":"new_password"
}
``` 
	- Response: __EXCEPTIONED_GENERIC_STATUS_RESPONSE_FORMAT__
> __HTTP/1.1 200 OK__
```
{
  "meta": "",
  "data": {
  "email ":"nimesh.aug11@gmail.com"
  }
}
``` 
> __HTTP/1.1 404 Not Found__: Use Generic Response
> __HTTP/1.1 400 Bad Request__: 
If the user email and token are not correct  
```
{
	"meta":"",
	"data":{
		"error_message": "Your email or token are invalid"
	}
}
```

#### Loggedin APIs

14.1
	- API Name: Profile API
	- Status: Need to be discuss URL
	- URL: /user/123/profile/
	- Method: GET
	- Header: Loggedin-Platform-Header
	- Request: Query Params None
	- Response: __EXCEPTIONED_GENERIC_STATUS_RESPONSE_FORMAT__
> __HTTP/1.1 200 OK__
```
{
  "meta": "",
  "data": {
    "customer_id": {
      "value": 123,
      "is_editable": false
    },
    "full_name": {
      "value": "Nimesh Kiran Verma",
      "is_editable": true
    },
    "mobile_number": {
      "value": "9911616971",
      "is_editable": true
    },
    "email": {
      "value": "nimesh.aug11@gmail.com",
      "is_editable": true
    },
    "city_id": {
      "value": 1,
      "is_editable": true
    },
    "class_id": {
      "value": 1,
      "is_editable": false
    },
    "school": {
      "value": "St Xaviers Sr Sec School",
      "is_editable": true
    },
    "profile_pic": {
      "value": "https://9gag.com/gag/a5nEdzg",
      "is_editable": true
    }
  }
}
```

14.2
	- API Name: Profile API
	- Status: Need to be discuss URL
	- URL: /user/profile/
	- Method: POST
Header: Loggedin-Platform-Header
Why 	- are we returning the same thing
	- Request: __ALL_GENERIC_STATUS_RESPONSE_FORMAT__
```
{
  "customer_id": 123,
  "full_name": "Nimesh Kiran Verma",
  "mobile_number": "9911616971",
  "email": "nimesh.aug11@gmail.com",
  "city_id": 1,
  "class_id": 1,
  "school": "St Xaviers Sr Sec School",
  "profile_pic": "https://9gag.com/gag/a5nEdzg"
}
```
	- Response: __ALL_GENERIC_STATUS_RESPONSE_FORMAT__
> __HTTP/1.1 200 OK__
```
{
  "meta": "",
  "data": {
    "customer_id": {
      "value": 123,
      "is_editable": false
    },
    "full_name": {
      "value": "Nimesh Kiran Verma",
      "is_editable": true
    },
    "mobile_number": {
      "value": "9911616971",
      "is_editable": true
    },
    "email": {
      "value": "nimesh.aug11@gmail.com",
      "is_editable": true
    },
    "city_id": {
      "value": 1,
      "is_editable": true
    },
    "class_id": {
      "value": 1,
      "is_editable": false
    },
    "school": {
      "value": "St Xaviers Sr Sec School",
      "is_editable": true
    },
    "profile_pic": {
      "value": "https://9gag.com/gag/a5nEdzg",
      "is_editable": true
    }
  }
}
```

15.
	- API Name: Change Password API
	- Status: Need to be discuss URL
	- URL: /user/123/password/
	- Method: POST
	- Header: Loggedin-Platform-Header
	- Request: __ALL_GENERIC_STATUS_RESPONSE_FORMAT__
```
{
    "customer_id": 123,
    "old_password": "pass123",
    "new_password": "newpass123"
}
```
	- Response: __ALL_GENERIC_STATUS_RESPONSE_FORMAT__
> __HTTP/1.1 200 OK__
```
{
  "meta": "",
  "data": {}
}
```

16.
	- API Name: Order API
	- Status: Need to be discuss URL
	- URL: /user/123/orders/
	- Method: POST
	- Header: Loggedin-Platform-Header
	- Request: None
Remark: If the customer has enrolled through the school the **amount** will be the price paid to the school otherwise it will be price they paid after applying both special offer and the coupon code to us without subtracting the wallet amount
	- Response: __ALL_GENERIC_STATUS_RESPONSE_FORMAT__
> __HTTP/1.1 200 OK__
```
{
  "meta": "",
  "data": {
    "orders": [
      {
        "order_no": "1",
        "amount": 1444,
        "details": "jvckdjsjvaxncs x",
        "purchase_date": "20/11/2017"
      },
      {
        "order_no": "1",
        "amount": 1444,
        "details": "jvckdjsjvaxncs x",
        "purchase_date": "20/11/2017"
      },
      {
        "order_no": "1",
        "amount": 1444,
        "details": "jvckdjsjvaxncs x",
        "purchase_date": "20/11/2017"
      },
      {
        "order_no": "1",
        "amount": 1444,
        "details": "jvckdjsjvaxncs x",
        "purchase_date": "20/11/2017"
      },
      {
        "order_no": "1",
        "amount": 1444,
        "details": "jvckdjsjvaxncs x",
        "purchase_date": "20/11/2017"
      }
    ]
  }
}
```

17.
	- API Name: Refer API
	- Status: Need to be discuss URL
	- URL: /user/123/refer/
	- Method: GET
	- Header: Loggedin-Platform-Header
	- Request: Query Params None
	- Response: __ALL_GENERIC_STATUS_RESPONSE_FORMAT__
> __HTTP/1.1 200 OK__
```
{
	"meta": "",
	"data": {
		"referral_earnings": 100,
		"referral_message": {
			"email": {
				"subject": "some text",
				"body": "Hi - wanted to share this very interesting Logical Reasoning Competition designed by IIT-IIM alumni, to initiate kids into logical thinking.  I think it provides a great exposure to kids. %0aThe exam is designed to stimulate the analytical thinking in kids and is conducted for SrKG to Class 9 kids. For Sr KG and Grade 1 kids, their invigilators read and explain the question to kids.%0aYou could DOWNLOAD a FREE SAMPLE PAPER from the link below: https://www.logiqids.com/user/register?c=Nimesh773"
			},
			"facebook": {
				"message": "https://www.facebook.com/v2.3/dialog/feed?app_id=1855999688021475&caption=Logiqids.com&description=%20Download%20Free%20Sample%20Paper%20for%20LogIQids%20Logical%20Reasoning%20Exam%20.&link=https://www.logiqids.com/user/register?c=Nimesh773&name=Must%20Try%20For%20Parents%20of%205%20to%2012%20Year%20Old%20Children!&picture=https://www.logiqids.com/images/LogIQids_FB_final1.png"
			},
			"sms": {
				"message": "Hi - wanted to share this very interesting Logical Reasoning Competition designed by IIT-IIM alumni, to initiate kids into logical thinking.  I think it provides a great exposure to kids. %0aThe exam is designed to stimulate the analytical thinking in kids and is conducted for SrKG to Class 9 kids. For Sr KG and Grade 1 kids, their invigilators read and explain the question to kids.%0aYou could DOWNLOAD a FREE SAMPLE PAPER from the link below: https://www.logiqids.com/user/register?c=Nimesh773"
			}
		}
	}
}
```

18.
	#CHECK_THIS
	- API Name: Refer SMS API
	- Status: Need to be discuss URL
	- URL: /user/123/refer/getsms
	- Method: POST
	- Header: Loggedin-Platform-Header
	- Request:
```
{
	"phone_number": 9999999999
}
```
	- Response: __ALL_GENERIC_STATUS_RESPONSE_FORMAT__
> __HTTP/1.1 200 OK__
```
{
	"meta": "",
	"data": {
		"sms_sent_success":true,
		"message": "The refer link has been sent to"  
	}
}
```

19.
	- API Name: User Account Info
	- Status: Need to be discuss URL
	- URL: /user/123/account/
	- Method: GET
	- Header: Loggedin-Platform-Header
	- Request: 
	- Response: __ALL_GENERIC_STATUS_RESPONSE_FORMAT__
> __HTTP/1.1 200 OK__
```
{
  "meta": "",
  "data": {
    "wallet":{
        "balance":900,
        "spendable":400,
    },
    "city_id": 1,
    "products": {
      "test": [
        {
          "package_id": 123,
          "name": "Mumbai 23 Dec Test",
          "subscription_date": "dd/mm/yyyy",
          "active": true
        },
        {
          "package_id": 124,
          "name": "Mumbai 29 Dec Test",
          "subscription_date": "dd/mm/yyyy",
          "active": false
        }
      ],
      "content": [
        {
          "package_id": 123,
          "name": "Annual Content",
          "subscription_date": "dd/mm/yyyy"
        },
        {
          "package_id": 124,
          "name": "Summer Content",
          "subscription_date": "dd/mm/yyyy",
          "active": false
        }
      ]
    }
  }
}
```

20.
	- API Name: Mega Menu
	- Status: Need to be discuss URL
	- URL: /user/id/menu
	- Method: GET
	- Header: Loggedin-Platform-Header
	- Request:
	- Response: __ALL_GENERIC_STATUS_RESPONSE_FORMAT__
```
{
  "meta": "",
  "data": [
      {
        "name": "Home",
        "url": "http://…..",
        "active": true,
        "children": []
      },
      {
        "name": "Test",
        "url": "http://…..",
        "active": true,
        "children": [
          {
            "name": "Sample Paper",
            "url": "http://…..",
            "active": true,
            "children": []
          },
          {
            "name": "Topic Notes",
            "url": "http://…..",
            "active": true,
            "children": []
          }
        ]
      },
      {
        "name": "Content",
        "url": "http://…..",
        "active": true,
        "children": []
      },
      {
        "name": "Account",
        "url": "http://…..",
        "active": true,
        "children": []
      },
        {
        "name": "Badges",
        "url": "http://…..",
        "active": true,
        "children": []
      }
    ]
}
```
21.
	- API Name: Order Review API
	- Status: Need to be discuss URL
	- URL: /user/123/order/review/
	- Method: POST
	- Header: Loggedin-Platform-Header
	- Request: __ALL_GENERIC_STATUS_RESPONSE_FORMAT__
```
{
  "package_ids": [
  23,
  24
  ],
//  "test": true,
//  "content": true
}
```
	- Response: __ALL_GENERIC_STATUS_RESPONSE_FORMAT__
```
{
  "meta": "",
  "data": {
    "discount":200,
    "package_data": [
      {
        "id": 23,
        "image_url":"jvhdsxkddsx",
        "name": "LogIQids Logical Reasoning Exam",
        "class_name": "Class 5",
        "academic_session": "2017-18",
        "info": "Mumbai",
        "price": 550
      },
      {
        "id": 24,
        "image_url":"jvhdsxkddsx",
        "name": "Content Package",
        "class_name": "Class 5",
        "academic_session": "2017-18",
        "info": "Package Valid upto Dec 31 2017",
        "price": 900
      }
    ]
  }
}
```
 
22.
	- API Name: Coupon API
	- Status: Need to be discuss URL
	- URL: /coupon/
	- Method: POST
	- Header: Loggedin-Platform-Header
	- Request:
```
{
  "Coupon_code": LOGIQ100,
}
```
	- Response: __ALL_GENERIC_STATUS_RESPONSE_FORMAT__
```
{
  "meta": "",
  "data": {
    "valid_request": true or false,
    "price":3000
  }
}
```
23. 
	- API Name: Checkout API
	- Status: Need to be discuss URL
	- URL: /user/123/checkout/
	- Method: POST
	- Header: Loggedin-Platform-Header
	- Request:
```
{
 "package_ids": [
      23,
      24
  ],
  "coupon_code": "LOGIQ100",
  "wallet_applied":true
}
```
	- Response: __ALL_GENERIC_STATUS_RESPONSE_FORMAT__
```
{
  "meta": "",
  "data": {
    "order_id": 1,
    "amount": 1212
  }
}
```

23. 
	- API Name: Payment Details API
	- Status: Need to be discuss URL
	- URL: /user/123/payment_details/
	- Method: POST
	- Header: Loggedin-Platform-Header
	- Request: 
```
{
  "order_id": 123
  "state_id": 1
}
```
	- Response: __ALL_GENERIC_STATUS_RESPONSE_FORMAT__
```
{
  "meta": "",
  "data": {
    "order_id": 1,
    "amount": 1212
  }
}
```



====================================================================================













































20
	- API Name: Weekly leaderboard API
	- Status: Need to be discuss URL
	- URL: /results/toppers/weekly/
	- Method: GET
	- Header: Loggedin-Platform-Header
	- Request:None
	- Response: __ALL_GENERIC_STATUS_RESPONSE_FORMAT__
```
{
  "meta": "",
  "data": {
    "students":[
      {
      "name":"Neha Yogesh Sane",
      "school":"XYZ",
      "score":50,
      "rank":1
      },
        {
      "name":"Neha1 Yogesh Sane",
      "school":"XYZ",
      "score":50,
      "rank":2
      },
      {
      "name":"Neha2 Yogesh Sane",
      "school":"XYZ",
      "score":50,
      "rank":3
      }
    ],
    "schools":[
      {
      "name":"XYZ",
      "score":50,
      "rank":1
      },
        {
      "name":"XYZ2",
      "score":50,
      "rank":2
      },
      {
      "name":"XYZ3",
      "score":50,
      "rank":3
      }
    ]
  }
}
```

21
	- API Name: Topic Notes API
	- Status: Need to be discuss URL
	- URL: /test/topic_notes/
	- Method: POST
	- Header: Loggedin-Platform-Header
	- Request: None
	- Response: __ALL_GENERIC_STATUS_RESPONSE_FORMAT__
```
{
  "meta": "",
  "data": {
    "topic_notes": [
      {
        "name": "Topic Note 1",
        "url": "https://www.teamten.com/lawrence/writings/coding-machines/",
        "upload_date":"22/09/2014"
      },
      {
        "name": "Topic Note 2",
        "url": "https://www.teamten.com/lawrence/writings/coding-machines/"
        "upload_date":"22/09/2014"
      },
      {
        "name": "Topic Note 3",
        "url": "https://www.teamten.com/lawrence/writings/coding-machines/"
        "upload_date":"22/09/2014"
      },
      {
        "name": "Topic Note 4",
        "url": "https://www.teamten.com/lawrence/writings/coding-machines/"
        "upload_date":"22/09/2014"
      },
      {
        "name": "Topic Note 5",
        "url": "https://www.teamten.com/lawrence/writings/coding-machines/"
        "upload_date":"22/09/2014"
      }
    ]
  }
}
```

22
	- API Name: Current Test Schedule API
	- Status: Need to be discuss URL
	- URL: /test/scheduel/
	- Method: POST
	- Header: Loggedin-Platform-Header
	- Request: None
	- Response: __ALL_GENERIC_STATUS_RESPONSE_FORMAT__
```
{
  "meta": "",
  "data": {
    "heading": "LogIQids Logical Reasoning Exam 2017-18, Mumbai",
    "messages": [
      "Tentative Schedule For Mumbai",
      "Level 1: Scheduled in Nov - Dec 2017 (Exact date to depend on the centre)",
      "Level 2: Scheduled in April 2018 (only for eligible candidates)",
      "The detailed schedule for the Test will be shared in due course. Please check out this space for further updates."
    ],
    "email": [
      "support@logiqids.com"
    ],
    "phone": [
      "+ 91 7045345345",
      "+ 91 8080809604"
    ]
  }
}
```

23
	- API Name: Sample Paper Status API
	- Status: Need to be discuss URL
	- URL: /test/sample_paper/status/
	- Method: POST
	- Header: Loggedin-Platform-Header
	- Request: None
	- Response: __ALL_GENERIC_STATUS_RESPONSE_FORMAT__
```
{
  "meta": "",
  "data": {
    "sample_paper_status": [
      {
        "sample_paper_1": {
          "id":123,
          "online_test": "not_started/started/completed",
          "offline_test": "not_started/started/completed"
        }
      },
      {
        "sample_paper_2": {
          "id":123,
          "online_test": "not_started/started/completed",
          "offline_test": "not_started/started/completed"
        }
      },
      {
        "sample_paper_3": {
          "id":123,
          "online_test": "not_started/started/completed",
          "offline_test": "not_started/started/completed"
        }
      },
      {
        "sample_paper_4": {
          "id":123,
          "online_test": "not_started/started/completed",
          "offline_test": "not_started/started/completed"
        }
      }
    ]
  }
}
```

pic_a


pic_b


pic_c


pic_d

24.
	- API Name: Sample Paper Download API
	- Status: Need to be discuss URL
	- URL: /test/sample_paper/<sample_paper_id>/
	- Method: POST
	- Header: Loggedin-Platform-Header
	- Request: None
	- Response: __ALL_GENERIC_STATUS_RESPONSE_FORMAT__
```
{
  "meta": "",
  "data": {
// Multipart form
}
}
```

25.
	- API Name: Sample Paper Solutions Download API
	- Status: Need to be discuss URL
	- URL: /test/sample_paper/<sample_paper_id>/solutions/
	- Method: POST
	- Header: Loggedin-Platform-Header
	- Request: None
	- Response: __ALL_GENERIC_STATUS_RESPONSE_FORMAT__
```
{
  "meta": "",
  "data": {
// Multipart form
}
}
```

26
	- API Name: Sample Paper Answers Submit API
	- Status: Need to be discuss URL
	- URL: /test/sample_paper/<sample_paper_id>/answers/
	- Method: POST
	- Header: Loggedin-Platform-Header
	- Request: 
```
{
  "answers": [
    {
      "question_id": 123,
      "question_serial_number": 1,
      "answer": "a"
    },
    {
      "question_id": 124,
      "question_serial_number": 2,
      "answer": "a"
    },
    {
      "question_id": 125,
      "question_serial_number": 3,
      "answer": "a"
    },
    {
      "question_id": 126,
      "question_serial_number": 4,
      "answer": "a"
    },
    {
      "question_id": 127,
      "question_serial_number": 5,
      "answer": "a"
    },
    {
      "question_id": 128,
      "question_serial_number": 6,
      "answer": "a"
    }
  ]
}
```

	- Response: __ALL_GENERIC_STATUS_RESPONSE_FORMAT__
```
{
  "meta": "",
  "data": {}
}
```

25.2
	- API Name: Sample Paper Answers Submit API
	- Status: Need to be discuss URL
	- URL: /test/sample_paper/<sample_paper_id>/answers/
	- Method: GET
	- Header: Loggedin-Platform-Header
	- Request: None
	- Response: __ALL_GENERIC_STATUS_RESPONSE_FORMAT__
```
{
  "meta": "",
  "data": {
    "question_data": {
      "count": 35,
      "answers": [{
          "question_id": 124,
          "question_serial_number": 2,
          "answer": "a"
        },
        {
          "question_id": 124,
          "question_serial_number": 2,
          "answer": "a"
        },
        {
          "question_id": 124,
          "question_serial_number": 2,
          "answer": "a"
        }

      ]
    }
  }
}
```

27
	- API Name: Sample Paper Attempt complete API
	- Status: Need to be discuss URL
	- URL: /test/sample_paper/<sample_paper_id>/attempt/
	- Method: POST
	- Header: Loggedin-Platform-Header
	- Request: None
	- Response: __ALL_GENERIC_STATUS_RESPONSE_FORMAT__
```
{
  "meta": "",
  "data": {
}
}
```

28.1
	- API Name: Sample Paper Question API
	- Status: Need to be discuss URL
	- URL: /test/sample_paper/<sample_paper_id>/question/<question_id>/
	- Method: GET
	- Header: Loggedin-Platform-Header
	- Request: None
	- Response: __ALL_GENERIC_STATUS_RESPONSE_FORMAT__
```
{
  "meta": "",
  "data": {
    "question": {
      "text": "Which of these sequences follows the pattern where each term (of course, other than the first term!!) is six more than the previous term?",
      "hint": "help",
      "image": ""
    },
    "options": [
      {
        "id": "a",
        "text": "A . 17, 23, 29, 35, 41",
        "image": ""
      },
      {
        "id": "b",
        "text": "B . 17, 23, 29, 35, 41",
        "image": ""
      },
      {
        "id": "c",
        "text": "C . 17, 23, 29, 35, 41",
        "image": ""
      },
      {
        "id": "d",
        "text": "D . 17, 23, 29, 35, 41",
        "image": ""
      }
    ]
  }
}
```

29
	- API Name: Sample Paper Question Answer API
	- Status: Need to be discuss URL
	- URL: /test/sample_paper/<sample_paper_id>/question/<question_id>/answer
	- Method: POST
	- Header: Loggedin-Platform-Header
	- Request: 
```
{
  "answer_id":"a"
}
```
	- Response: __ALL_GENERIC_STATUS_RESPONSE_FORMAT__
```
{
  "meta": "",
  "data": {}
}
```
30
	- API Name: Sample Paper Analysis API
	- Status: Need to be discuss URL
	- URL: /test/sample_paper/<sample_paper_id>/analysis/
	- Method: POST
	- Header: Loggedin-Platform-Header
	- Request: None
	- Response: __ALL_GENERIC_STATUS_RESPONSE_FORMAT__
```
{
  "meta": "",
  "data": {
    "result": {
      "total_questions": 35,
      "attempted": 10,
      "correct_answers": 5,
      "score": 10.0
    },
    "analysis": [{
        "question_number": 1,
        "topic": {
          "name": "verbal",
          "id": 1
        },
        "image": "www.xszvxzk.coskmx/asix",
        "hint": "cdcds",
        "question_description": "Which of the below mentioned sequences DOES NOT follow the order – sum of any two consecutive numbers is an odd number?",
        "user_answer": "a",
        "correct_answer": "a",
        "solution": "In option D, the 4th and 5th terms are 2 and 2 and their sum is 4 which is an even number. Hence, the correct answer is option D",
        "options": [{
            "id": "a",
            "text": "A . 17, 23, 29, 35, 41",
            "image": ""
          },
          {
            "id": "b",
            "text": "B . 17, 23, 29, 35, 41",
            "image": ""
          },
          {
            "id": "c",
            "text": "C . 17, 23, 29, 35, 41",
            "image": ""
          },
          {
            "id": "d",
            "text": "D . 17, 23, 29, 35, 41",
            "image": ""
          }

        ]
      },
      {
        "question_number": 1,
        "topic": {
          "name": "verbal",
          "id": 1
        },
        "image": "www.xszvxzk.coskmx/asix",
        "hint": "cdcds",
        "question_description": "Which of the below mentioned sequences DOES NOT follow the order – sum of any two consecutive numbers is an odd number?",
        "user_answer": "a",
        "correct_answer": "a",
        "solution": "In option D, the 4th and 5th terms are 2 and 2 and their sum is 4 which is an even number. Hence, the correct answer is option D",
        "options": [{
            "id": "a",
            "text": "A . 17, 23, 29, 35, 41",
            "image": ""
          },
          {
            "id": "b",
            "text": "B . 17, 23, 29, 35, 41",
            "image": ""
          },
          {
            "id": "c",
            "text": "C . 17, 23, 29, 35, 41",
            "image": ""
          },
          {
            "id": "d",
            "text": "D . 17, 23, 29, 35, 41",
            "image": ""
          }

        ]
      },
      {
        "question_number": 1,
        "topic": {
          "name": "verbal",
          "id": 1
        },
        "image": "www.xszvxzk.coskmx/asix",
        "hint": "cdcds",
        "question_description": "Which of the below mentioned sequences DOES NOT follow the order – sum of any two consecutive numbers is an odd number?",
        "user_answer": "a",
        "correct_answer": "a",
        "solution": "In option D, the 4th and 5th terms are 2 and 2 and their sum is 4 which is an even number. Hence, the correct answer is option D",
        "options": [{
            "id": "a",
            "text": "A . 17, 23, 29, 35, 41",
            "image": ""
          },
          {
            "id": "b",
            "text": "B . 17, 23, 29, 35, 41",
            "image": ""
          },
          {
            "id": "c",
            "text": "C . 17, 23, 29, 35, 41",
            "image": ""
          },
          {
            "id": "d",
            "text": "D . 17, 23, 29, 35, 41",
            "image": ""
          }

        ]
      },
      {
        "question_number": 1,
        "topic": {
          "name": "verbal",
          "id": 1
        },
        "image": "www.xszvxzk.coskmx/asix",
        "hint": "cdcds",
        "question_description": "Which of the below mentioned sequences DOES NOT follow the order – sum of any two consecutive numbers is an odd number?",
        "user_answer": "a",
        "correct_answer": "a",
        "solution": "In option D, the 4th and 5th terms are 2 and 2 and their sum is 4 which is an even number. Hence, the correct answer is option D",
        "options": [{
            "id": "a",
            "text": "A . 17, 23, 29, 35, 41",
            "image": ""
          },
          {
            "id": "b",
            "text": "B . 17, 23, 29, 35, 41",
            "image": ""
          },
          {
            "id": "c",
            "text": "C . 17, 23, 29, 35, 41",
            "image": ""
          },
          {
            "id": "d",
            "text": "D . 17, 23, 29, 35, 41",
            "image": ""
          }

        ]
      }
    ]

  }
}
```


31
	- API Name: Sample Paper Analysis API
	- Status: Need to be discuss URL
	- URL: /test/sample_paper/analysis/
	- Method: POST
	- Header: Loggedin-Platform-Header
	- Request: None
	- Response: __ALL_GENERIC_STATUS_RESPONSE_FORMAT__
{
  "meta": "",
  "data": {
    "comparative": [{
        "candidate": "user",
        "score_percentage": 50,
        "accuracy_percentage": 50,
        "papers_attempted": 3
      },
      {
        "candidate": "average",
        "score_percentage": 50,
        "accuracy_percentage": 50,
        "papers_attempted": 3
      },
      {
        "candidate": "topper",
        "score_percentage": 50,
        "accuracy_percentage": 50,
        "papers_attempted": 3
      }
    ],
    "paper_score": [{
        "id": 1,
        "score_percentage": 50,
        "accuracy_percentage": 50,
        "papers_attempted": 3
      },
      {
        "id": 2,
        "score_percentage": 50,
        "accuracy_percentage": 50,
        "papers_attempted": 3
      },
      {
        "id": 3,
        "score_percentage": 50,
        "accuracy_percentage": 50,
        "papers_attempted": 3
      },
      {
        "id": 4,
        "score_percentage": 50,
        "accuracy_percentage": 50,
        "papers_attempted": 3
      }
    ],
    "topicwise_score": [{
        "name": "verbal",
        "id": 1,
        "score_percentage": 50,
        "accuracy_percentage": 50,
        "papers_attempted": 3
      },
      {
        "name": "verbal",
        "id": 2,
        "score_percentage": 50,
        "accuracy_percentage": 50,
        "papers_attempted": 3
      },
      {
        "name": "verbal",
        "id": 3,
        "score_percentage": 50,
        "accuracy_percentage": 50,
        "papers_attempted": 3
      },
      {
        "name": "verbal",
        "id": 4,
        "score_percentage": 50,
        "accuracy_percentage": 50,
        "papers_attempted": 3
      }
    ]
  }
}

32
	- API Name: Past Test Analysis API
	- Status: Need to be discuss URL
	- URL: /test/past/analysis/
	- Method: POST
	- Header: Loggedin-Platform-Header
	- Request: None
	- Response: __ALL_GENERIC_STATUS_RESPONSE_FORMAT__
{
  "meta": "",
  "data": {
    "past_tests":[
      {
        "id":54,
        "heading":"LogIQids Final Stage Test 2017",
        "date":"24/12/2017",
        "result":[
        {
          "name":"Score Percentage",
          "value":79.09
        },
        {
          "name":"Total Marks",
          "value":120
        },
        {
          "name":"User Marks",
          "value":80
        },
        {
          "name":"Rank Within City",
          "value":1
        },
        {
          "name":"Rank Across City",
          "value":1
        },
        {
          "name":"Accuracy Percentage",
          "value":10
        },
        {
          "name":"Score Percentage",
          "value":1
        }

        ]
      },
      {
        "id":54,
        "heading":"LogIQids Final Stage Test 2017",
        "date":"24/12/2017",
        "result":[
        {
          "name":"Score Percentage",
          "value":79.09
        },
        {
          "name":"Total Marks",
          "value":120
        },
        {
          "name":"User Marks",
          "value":80
        },
        {
          "name":"Rank Within City",
          "value":1
        },
        {
          "name":"Rank Across City",
          "value":1
        },
        {
          "name":"Accuracy Percentage",
          "value":10
        },
        {
          "name":"Score Percentage",
          "value":1
        }

        ]
      },
      {
        "id":54,
        "heading":"LogIQids Final Stage Test 2017",
        "date":"24/12/2017",
        "result":[
        {
          "name":"Score Percentage",
          "value":79.09
        },
        {
          "name":"Total Marks",
          "value":120
        },
        {
          "name":"User Marks",
          "value":80
        },
        {
          "name":"Rank Within City",
          "value":1
        },
        {
          "name":"Rank Across City",
          "value":1
        },
        {
          "name":"Accuracy Percentage",
          "value":10
        },
        {
          "name":"Score Percentage",
          "value":1
        }

        ]
      },
    ]

  }
}


33
	- API Name: Past Test Detailed Analysis API
	- Status: Need to be discuss URL
	- URL: /test/<test_id>/analysis/
	- Method: POST
	- Header: Loggedin-Platform-Header
	- Request: None
	- Response: __ALL_GENERIC_STATUS_RESPONSE_FORMAT__
{
  "meta": "",
  "data": {
    "overall_result": [{
        "id": 54,
        "heading": "LogIQids Final Stage Test 2017",
        "date": "24/12/2017",
        "result": [{
            "name": "Score Percentage",
            "value": {
              "user": 41,
              "average": 42
            }
          },
          {
            "name": "Total Marks",
            "value": {
              "user": "108/120",
              "average": "112/120"
            }
          },

          {
            "name": "Rank Within City",
            "value": {
              "user": 1,
              "average": 10
            }
          },
          {
            "name": "Rank Across City",
            "value": {
              "user": 1,
              "average": 10
            }
          },
          {
            "name": "Accuracy Percentage",
            "value": {
              "user": 41,
              "average": 13
            }
          },
          {
            "name": "Score Percentage",
            "value": {
              "user": 31,
              "average": 21
            }
          }

        ]
      },
      {
        "id": 54,
        "heading": "LogIQids Final Stage Test 2017",
        "date": "24/12/2017",
        "result": [{
            "name": "Score Percentage",
            "value": 79.09
          },
          {
            "name": "Total Marks",
            "value": 120
          },
          {
            "name": "User Marks",
            "value": 80
          },
          {
            "name": "Rank Within City",
            "value": 1
          },
          {
            "name": "Rank Across City",
            "value": 1
          },
          {
            "name": "Accuracy Percentage",
            "value": 10
          },
          {
            "name": "Score Percentage",
            "value": 1
          }

        ]
      },
      {
        "id": 54,
        "heading": "LogIQids Final Stage Test 2017",
        "date": "24/12/2017",
        "result": [{
            "name": "Score Percentage",
            "value": 79.09
          },
          {
            "name": "Total Marks",
            "value": 120
          },
          {
            "name": "User Marks",
            "value": 80
          },
          {
            "name": "Rank Within City",
            "value": 1
          },
          {
            "name": "Rank Across City",
            "value": 1
          },
          {
            "name": "Accuracy Percentage",
            "value": 10
          },
          {
            "name": "Score Percentage",
            "value": 1
          }

        ]
      }
    ],
    "analysis": [{
        "question_number": 1,
        "topic": {
          "name": "verbal",
          "id": 1
        },
        "image": "www.xszvxzk.coskmx/asix",
        "hint": "cdcds",
        "question_description": "Which of the below mentioned sequences DOES NOT follow the order – sum of any two consecutive numbers is an odd number?",
        "user_answer": "a",
        "correct_answer": "a",
        "solution": "In option D, the 4th and 5th terms are 2 and 2 and their sum is 4 which is an even number. Hence, the correct answer is option D",
        "options": [{
            "id": "a",
            "text": "A . 17, 23, 29, 35, 41",
            "image": ""
          },
          {
            "id": "b",
            "text": "B . 17, 23, 29, 35, 41",
            "image": ""
          },
          {
            "id": "c",
            "text": "C . 17, 23, 29, 35, 41",
            "image": ""
          },
          {
            "id": "d",
            "text": "D . 17, 23, 29, 35, 41",
            "image": ""
          }

        ]
      },
      {
        "question_number": 1,
        "topic": {
          "name": "verbal",
          "id": 1
        },
        "image": "www.xszvxzk.coskmx/asix",
        "hint": "cdcds",
        "question_description": "Which of the below mentioned sequences DOES NOT follow the order – sum of any two consecutive numbers is an odd number?",
        "user_answer": "a",
        "correct_answer": "a",
        "solution": "In option D, the 4th and 5th terms are 2 and 2 and their sum is 4 which is an even number. Hence, the correct answer is option D",
        "options": [{
            "id": "a",
            "text": "A . 17, 23, 29, 35, 41",
            "image": ""
          },
          {
            "id": "b",
            "text": "B . 17, 23, 29, 35, 41",
            "image": ""
          },
          {
            "id": "c",
            "text": "C . 17, 23, 29, 35, 41",
            "image": ""
          },
          {
            "id": "d",
            "text": "D . 17, 23, 29, 35, 41",
            "image": ""
          }

        ]
      },
      {
        "question_number": 1,
        "topic": {
          "name": "verbal",
          "id": 1
        },
        "image": "www.xszvxzk.coskmx/asix",
        "hint": "cdcds",
        "question_description": "Which of the below mentioned sequences DOES NOT follow the order – sum of any two consecutive numbers is an odd number?",
        "user_answer": "a",
        "correct_answer": "a",
        "solution": "In option D, the 4th and 5th terms are 2 and 2 and their sum is 4 which is an even number. Hence, the correct answer is option D",
        "options": [{
            "id": "a",
            "text": "A . 17, 23, 29, 35, 41",
            "image": ""
          },
          {
            "id": "b",
            "text": "B . 17, 23, 29, 35, 41",
            "image": ""
          },
          {
            "id": "c",
            "text": "C . 17, 23, 29, 35, 41",
            "image": ""
          },
          {
            "id": "d",
            "text": "D . 17, 23, 29, 35, 41",
            "image": ""
          }

        ]
      },
      {
        "question_number": 1,
        "topic": {
          "name": "verbal",
          "id": 1
        },
        "image": "www.xszvxzk.coskmx/asix",
        "hint": "cdcds",
        "question_description": "Which of the below mentioned sequences DOES NOT follow the order – sum of any two consecutive numbers is an odd number?",
        "user_answer": "a",
        "correct_answer": "a",
        "solution": "In option D, the 4th and 5th terms are 2 and 2 and their sum is 4 which is an even number. Hence, the correct answer is option D",
        "options": [{
            "id": "a",
            "text": "A . 17, 23, 29, 35, 41",
            "image": ""
          },
          {
            "id": "b",
            "text": "B . 17, 23, 29, 35, 41",
            "image": ""
          },
          {
            "id": "c",
            "text": "C . 17, 23, 29, 35, 41",
            "image": ""
          },
          {
            "id": "d",
            "text": "D . 17, 23, 29, 35, 41",
            "image": ""
          }

        ]
      }
    ]

  }
}


31
	- API Name: Sample Paper Analysis API
	- Status: Need to be discuss URL
	- URL: /content/package_subscribed/<package_subscribtion_id>/analysis/
	- Method: POST
	- Header: Loggedin-Platform-Header
	- Request: None
	- Response: __ALL_GENERIC_STATUS_RESPONSE_FORMAT__
{

  "meta": "",
  "data": {
    "coins": 34,
    "proficiency": {
      "user": 51,
      "average": 61,
      "topper": 82
    },
    "key_topics_to_focus": [{
        "id": 1,
        "name": "Multiple Instructions"
      },
      {
        "id": 1,
        "name": "Visual"
      },
      {
        "id": 1,
        "name": "Verbal"
      },
      {
        "id": 1,
        "name": "Puzzles"
      }
    ],
    "comparative": [{
        "candidate": "user",
        "score_percentage": 50,
        "accuracy_percentage": 50,
        "papers_attempted": 3
      },
      {
        "candidate": "average",
        "score_percentage": 50,
        "accuracy_percentage": 50,
        "papers_attempted": 3
      },
      {
        "candidate": "topper",
        "score_percentage": 50,
        "accuracy_percentage": 50,
        "papers_attempted": 3
      }
    ],
    "topicwise_score": [{
        "name": "verbal",
        "id": 1,
        "score_percentage": 50,
        "accuracy_percentage": 50,
        "papers_attempted": 3
      },
      {
        "name": "verbal",
        "id": 2,
        "score_percentage": 50,
        "accuracy_percentage": 50,
        "papers_attempted": 3
      },
      {
        "name": "verbal",
        "id": 3,
        "score_percentage": 50,
        "accuracy_percentage": 50,
        "papers_attempted": 3
      },
      {
        "name": "verbal",
        "id": 4,
        "score_percentage": 50,
        "accuracy_percentage": 50,
        "papers_attempted": 3
      }
    ]
  }
}



33
	- API Name: Topic API
	- Status: Need to be discuss URL
	- URL: /content/topics/
	- Method: POST
	- Header: Loggedin-Platform-Header
	- Request: None
	- Response: __ALL_GENERIC_STATUS_RESPONSE_FORMAT__
{

  "meta": "",
  "data": {
    "topics":[
      {
        "name":"Puzzles",
        "id":123,
        "icon":"www.vcds.com/dgvsj/xsgv",
        "objective":"To enchance child's ability to solve complex questions combining multiple skill-set or questions which involve a trick / smart thinking."
        },
      {
        "name":"Verbal",
        "id":123,
        "icon":"www.vcds.com/dgvsj/xsgv",
        "objective":"To enchance child's ability to solve complex questions combining multiple skill-set or questions which involve a trick / smart thinking."
        },
      {
        "name":"Visual",
        "id":123,
        "icon":"www.vcds.com/dgvsj/xsgv",
        "objective":"To enchance child's ability to solve complex questions combining multiple skill-set or questions which involve a trick / smart thinking."
        },
      {
        "name":"Trends/ Relationship",
        "id":123,
        "icon":"www.vcds.com/dgvsj/xsgv",
        "objective":"To enchance child's ability to solve complex questions combining multiple skill-set or questions which involve a trick / smart thinking."
        },
      {
        "name":"Conclusion",
        "id":123,
        "icon":"www.vcds.com/dgvsj/xsgv",
        "objective":"To enchance child's ability to solve complex questions combining multiple skill-set or questions which involve a trick / smart thinking."
      }

    ]
  }
}


34
	- API Name:Topic worksheet Status API
	- Status: Need to be discuss URL
	- URL: /content/topic/<topic_id>/worksheet/
	- Method: POST
	- Header: Loggedin-Platform-Header
	- Request: None
	- Response: __ALL_GENERIC_STATUS_RESPONSE_FORMAT__
{
  "meta": "",
  "data": {
          "id":123,
          "online_test": "not_started/started/completed",
          "offline_test": "not_started/started/completed"
  }
}


35
	- API Name:Topic worksheet Status API
	- Status: Need to be discuss URL
	- URL: /content/topic/<topic_id>/worksheet/
	- Method: POST
	- Header: Loggedin-Platform-Header
	- Request: None
	- Response: __ALL_GENERIC_STATUS_RESPONSE_FORMAT__
{
  "meta": "",
  "data": {
          "id":123,
          "online_test": "not_started/started/completed",
          "offline_test": "not_started/started/completed"
  }
}

36
	- API Name: Sample Paper Analysis API
	- Status: Need to be discuss URL
	- URL: /test/sample_paper/analysis/
	- Method: POST
	- Header: Loggedin-Platform-Header
	- Request: None
	- Response: __ALL_GENERIC_STATUS_RESPONSE_FORMAT__
{
  "meta": "",
  "data": {
    "comparative": [{
        "candidate": "user",
        "score_percentage": 50,
        "accuracy_percentage": 50,
        "number_of_question_attempted": 3
      },
      {
        "candidate": "average",
        "score_percentage": 50,
        "accuracy_percentage": 50,
        "number_of_question_attempted": 3
      },
      {
        "candidate": "topper",
        "score_percentage": 50,
        "accuracy_percentage": 50,
        "number_of_question_attempted": 3
      }
    ],
    "skill_proficiency": {
      "user": 50,
      "average": 60,
      "topper": 70
    },
    "performance_message": "Your overall score is 40%. Don't worry, as you continue practicing, we are sure you will be able to improve. Just carry on with your practice on a regular basis",
    "topicwise_score": [{
        "name": "verbal",
        "id": 1,
        "score_percentage": 50,
        "accuracy_percentage": 50,
        "papers_attempted": 3
      },
      {
        "name": "verbal",
        "id": 2,
        "score_percentage": 50,
        "accuracy_percentage": 50,
        "papers_attempted": 3
      },
      {
        "name": "verbal",
        "id": 3,
        "score_percentage": 50,
        "accuracy_percentage": 50,
        "papers_attempted": 3
      },
      {
        "name": "verbal",
        "id": 4,
        "score_percentage": 50,
        "accuracy_percentage": 50,
        "papers_attempted": 3
      }
    ]
  }
}

36
	- API Name: Topic Notes API
	- Status: Need to be discuss URL
	- URL: /test/topic/<topic_id>/notes/
	- Method: POST
	- Header: Loggedin-Platform-Header
	- Request: None
	- Response: __ALL_GENERIC_STATUS_RESPONSE_FORMAT__
{
  "meta": "",
  "data": {
    "topic_notes": [{
      "name": "Verbal Skills",
      "url": "www.wdd.dxsz/dgxvs/xh"
    }, {
      "name": "Verbal Skills",
      "url": "www.wdd.dxsz/dgxvs/xh"
    }]
  }
}

37
	- API Name: Topic Past worksheet API
	- Status: Need to be discuss URL
	- URL: /test/topic/past_worksheet/
	- Method: POST
	- Header: Loggedin-Platform-Header
	- Request: None
	- Response: __ALL_GENERIC_STATUS_RESPONSE_FORMAT__
{
  "meta": "",
  "data": {
    "worksheets": [{
        "id": 123,
        "class": "Class 5",
        "date": "18/07/2017",
        "topic": {
          "name": "Verbal",
          "id": 123
        },
        "score": 1,
        "status": "online_incomplete/offline_incomplete/online_complete/offline_complete"
      },
      {
        "id": 123,

        "class": "Class 5",
        "date": "18/07/2017",
        "topic": {
          "name": "Verbal",
          "id": 123
        },
        "score": 1,
        "status": "online_incomplete/offline_incomplete/online_complete/offline_complete"
      },
      {
        "id": 123,

        "class": "Class 5",
        "date": "18/07/2017",
        "topic": {
          "name": "Verbal",
          "id": 123
        },
        "score": 1,
        "status": "online_incomplete/offline_incomplete/online_complete/offline_complete"
      }
    ]
  }
}



38
	- API Name: Topic Past worksheet API
	- Status: Need to be discuss URL
	- URL: /test/topic/<topic_id>/past_worksheet/
	- Method: POST
	- Header: Loggedin-Platform-Header
	- Request: None
	- Response: __ALL_GENERIC_STATUS_RESPONSE_FORMAT__
{
  "meta": "",
  "data": {
    "worksheets": [{
        "id": 123,
        "class": "Class 5",
        "date": "18/07/2017",
        "topic": {
          "name": "Verbal",
          "id": 123
        },
        "score": 1,
        "status": "online_incomplete/offline_incomplete/online_complete/offline_complete"
      },
      {
        "id": 123,

        "class": "Class 5",
        "date": "18/07/2017",
        "topic": {
          "name": "Verbal",
          "id": 123
        },
        "score": 1,
        "status": "online_incomplete/offline_incomplete/online_complete/offline_complete"
      },
      {
        "id": 123,

        "class": "Class 5",
        "date": "18/07/2017",
        "topic": {
          "name": "Verbal",
          "id": 123
        },
        "score": 1,
        "status": "online_incomplete/offline_incomplete/online_complete/offline_complete"
      }
    ]
  }
}



------------------------------------------
























39
	- API Name: Worksheet Download API
	- Status: Need to be discuss URL
	- URL: /content/topic/<topic_id>/worksheet/<worksheet_id>
worksheet_id can be latest
	- Method: POST
	- Header: Loggedin-Platform-Header
	- Request: None
	- Response: __ALL_GENERIC_STATUS_RESPONSE_FORMAT__
{
  "meta": "",
  "data": {
// Multipart form
}
}

40
	- API Name: Worksheet Solutions Download API
	- Status: Need to be discuss URL
	- URL: /content/topic/<topic_id>/worksheet/<worksheet_id>/solutions/
worksheet_id can be latest
	- Method: POST
	- Header: Loggedin-Platform-Header
	- Request: None
	- Response: __ALL_GENERIC_STATUS_RESPONSE_FORMAT__
{
  "meta": "",
  "data": {
// Multipart form
}
}

41.1
	- API Name: Worksheet Answers Submit API
	- Status: Need to be discuss URL
	- URL: /content/topic/<topic_id>/answers/
	- Method: POST
	- Header: Loggedin-Platform-Header
	- Request: 
{
  "answers": [
    {
      "question_id": 123,
      "question_serial_number": 1,
      "answer": "a"
    },
    {
      "question_id": 124,
      "question_serial_number": 2,
      "answer": "a"
    },
    {
      "question_id": 125,
      "question_serial_number": 3,
      "answer": "a"
    },
    {
      "question_id": 126,
      "question_serial_number": 4,
      "answer": "a"
    },
    {
      "question_id": 127,
      "question_serial_number": 5,
      "answer": "a"
    },
    {
      "question_id": 128,
      "question_serial_number": 6,
      "answer": "a"
    }
  ]
}

	- Response: __ALL_GENERIC_STATUS_RESPONSE_FORMAT__
{
    "meta":"",
    "data":{
        "heading":"Topic : Puzzles Worksheet Download Date : 11-Jul-2017",
        "result":[
            {
                "name":"Question Asked",
                "value":15
            },
            {
                "name":"Attempted",
                "value":1
            },
            {
                "name":"Correct",
                "value":0
            },
            {
                "name":"Score",
                "value":0
            }
        ]
    }
}
```

41.2
	- API Name: Worksheet Answers Submit API
	- Status: Need to be discuss URL
	- URL:  /content/topic/<topic_id>/worksheet/<worksheet_id>/solutions/
	- Method: GET
	- Header: Loggedin-Platform-Header
	- Request: None
	- Response: __ALL_GENERIC_STATUS_RESPONSE_FORMAT__
```javascript
{
  "meta": "",
  "data": {
    "question_data": {
      "count": 35,
      "heading":"Topic: Puzzles Worksheet Download Date: 11-Jul-2017" ,
      "answers": [{
          "question_id": 124,
          "question_serial_number": 2,
          "answer": "a"
        },
        {
          "question_id": 124,
          "question_serial_number": 2,
          "answer": "a"
        },
        {
          "question_id": 124,
          "question_serial_number": 2,
          "answer": "a"
        }

      ]
    }
  }
}
```

43
	- API Name: Worksheet Attempt complete API
	- Status: Need to be discuss URL
	- URL:  /content/topic/<topic_id>/worksheet/<worksheet_id>/attempt/
worksheet_id can be latest
	- Method: POST
	- Header: Loggedin-Platform-Header
	- Request: None
	- Response: __ALL_GENERIC_STATUS_RESPONSE_FORMAT__
```javascript
{
  "meta": "",
  "data": {}
}
```

44
	- API Name: Worksheet Question API
	- Status: Need to be discuss URL
	- URL: /content/topic/<topic_id>/worksheet/<worksheet_id>/question/<question_id>/
	- Method: GET
	- Header: Loggedin-Platform-Header
	- Request: None
	- Response: __ALL_GENERIC_STATUS_RESPONSE_FORMAT__
```javascript
{
  "meta": "",
  "data": {
    "question": {
      "text": "Which of these sequences follows the pattern where each term (of course, other than the first term!!) is six more than the previous term?",
      "hint": "help",
      "image": ""
    },
    "options": [
      {
        "id": "a",
        "text": "A . 17, 23, 29, 35, 41",
        "image": ""
      },
      {
        "id": "b",
        "text": "B . 17, 23, 29, 35, 41",
        "image": ""
      },
      {
        "id": "c",
        "text": "C . 17, 23, 29, 35, 41",
        "image": ""
      },
      {
        "id": "d",
        "text": "D . 17, 23, 29, 35, 41",
        "image": ""
      }
    ]
  }
}
```

45
	- API Name: Worksheet Question Answer API
	- Status: Need to be discuss URL
	- URL: /content/topic/<topic_id>/worksheet/<worksheet_id>/question/<question_id>/answer
	- Method: POST
	- Header: Loggedin-Platform-Header
	- Request: 
```javascript
{
  "answer_id":"a"
}
```
	- Response: __ALL_GENERIC_STATUS_RESPONSE_FORMAT__
```javascript
{
  "meta": "",
  "data": {}
}
```

46
	- API Name: Worksheet Analysis API
	- Status: Need to be discuss URL
	- URL:/content/topic/<topic_id>/worksheet/<worksheet_id>/analysis/
	- Method: POST
	- Header: Loggedin-Platform-Header
	- Request: None
	- Response: __ALL_GENERIC_STATUS_RESPONSE_FORMAT__
```javascript
{
  "meta": "",
  "data": {
    "result": {
      "total_questions": 35,
      "attempted": 10,
      "correct_answers": 5,
      "score": 10.0
    },
    "analysis": [{
        "question_number": 1,
        "topic": {
          "name": "verbal",
          "id": 1
        },
        "image": "www.xszvxzk.coskmx/asix",
        "hint": "cdcds",
        "question_description": "Which of the below mentioned sequences DOES NOT follow the order – sum of any two consecutive numbers is an odd number?",
        "user_answer": "a",
        "correct_answer": "a",
        "solution": "In option D, the 4th and 5th terms are 2 and 2 and their sum is 4 which is an even number. Hence, the correct answer is option D",
        "options": [{
            "id": "a",
            "text": "A . 17, 23, 29, 35, 41",
            "image": ""
          },
          {
            "id": "b",
            "text": "B . 17, 23, 29, 35, 41",
            "image": ""
          },
          {
            "id": "c",
            "text": "C . 17, 23, 29, 35, 41",
            "image": ""
          },
          {
            "id": "d",
            "text": "D . 17, 23, 29, 35, 41",
            "image": ""
          }

        ]
      },
      {
        "question_number": 1,
        "topic": {
          "name": "verbal",
          "id": 1
        },
        "image": "www.xszvxzk.coskmx/asix",
        "hint": "cdcds",
        "question_description": "Which of the below mentioned sequences DOES NOT follow the order – sum of any two consecutive numbers is an odd number?",
        "user_answer": "a",
        "correct_answer": "a",
        "solution": "In option D, the 4th and 5th terms are 2 and 2 and their sum is 4 which is an even number. Hence, the correct answer is option D",
        "options": [{
            "id": "a",
            "text": "A . 17, 23, 29, 35, 41",
            "image": ""
          },
          {
            "id": "b",
            "text": "B . 17, 23, 29, 35, 41",
            "image": ""
          },
          {
            "id": "c",
            "text": "C . 17, 23, 29, 35, 41",
            "image": ""
          },
          {
            "id": "d",
            "text": "D . 17, 23, 29, 35, 41",
            "image": ""
          }

        ]
      },
      {
        "question_number": 1,
        "topic": {
          "name": "verbal",
          "id": 1
        },
        "image": "www.xszvxzk.coskmx/asix",
        "hint": "cdcds",
        "question_description": "Which of the below mentioned sequences DOES NOT follow the order – sum of any two consecutive numbers is an odd number?",
        "user_answer": "a",
        "correct_answer": "a",
        "solution": "In option D, the 4th and 5th terms are 2 and 2 and their sum is 4 which is an even number. Hence, the correct answer is option D",
        "options": [{
            "id": "a",
            "text": "A . 17, 23, 29, 35, 41",
            "image": ""
          },
          {
            "id": "b",
            "text": "B . 17, 23, 29, 35, 41",
            "image": ""
          },
          {
            "id": "c",
            "text": "C . 17, 23, 29, 35, 41",
            "image": ""
          },
          {
            "id": "d",
            "text": "D . 17, 23, 29, 35, 41",
            "image": ""
          }

        ]
      },
      {
        "question_number": 1,
        "topic": {
          "name": "verbal",
          "id": 1
        },
        "image": "www.xszvxzk.coskmx/asix",
        "hint": "cdcds",
        "question_description": "Which of the below mentioned sequences DOES NOT follow the order – sum of any two consecutive numbers is an odd number?",
        "user_answer": "a",
        "correct_answer": "a",
        "solution": "In option D, the 4th and 5th terms are 2 and 2 and their sum is 4 which is an even number. Hence, the correct answer is option D",
        "options": [{
            "id": "a",
            "text": "A . 17, 23, 29, 35, 41",
            "image": ""
          },
          {
            "id": "b",
            "text": "B . 17, 23, 29, 35, 41",
            "image": ""
          },
          {
            "id": "c",
            "text": "C . 17, 23, 29, 35, 41",
            "image": ""
          },
          {
            "id": "d",
            "text": "D . 17, 23, 29, 35, 41",
            "image": ""
          }

        ]
      }
    ]

  }
}
```
