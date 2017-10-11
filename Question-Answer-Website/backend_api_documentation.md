# API Documentation
#### Aim:
    This document aims to provide a general understanding of the backend APIs and its details.
#### Definitions:
 - LoggedIn-Header:
 - A header is defined as LoggedIn-Header when the header has the session token in it. This type of header is used for the user who is the registered and has logged into the system.

LoggedIn-Header JSON:
{
"session_token":"logiqid_34_mYrmAIJA6TUDqfOvpfqez7fM9Mp11n2b"
}
 
The session_token value follows the given pattern:
logiqid_<customer_id>_<uuid>
 
uuid = 32 Character unique text used for user identification
 
Platform-Header:
                      A header is defined as Platform-Header when the header has the information about the platform which is calling the API. This type of header is used for the cases when the same API needs to served differently for different Platforms.
 
Platform-Header JSON:
{
"source":"desktop_browser"
}
 
source can take any of the following values:
-    web: When the API is called from Desktop browser
-   mweb: When the API is called from Mobile browser
-   android: When the API is called from Android App
-   ios: When the API is called from IOS App
 


Versioning:
                      We will be utilising the URL based Versioning i.e we will use the version number in the URL.
 
In our system we will be having either:

 Loggedin-Platform-Header = Loggedin-Header + Platform-Header
{
"session_token":"logiqid_34_mYrmAIJA6TUDqfOvpfqez7fM9Mp11n2b",
"source":"desktop_browser"
}
 
 Platform-Header
{
"source":"desktop_browser"
}
  
Meta-Data-Response:
                      A response is called Meta-Data-Response when it satisfies the following JSON schema
{
"meta" : "This is used to provide any meta information about the API, mostly not used by clients (browsers/apps)",
"data" : {"data_key":"data value"
}
}
 
 







 

Miscellaneous APIs
1.
API Name: Reviews API
Status: Might not be required, need to be discussed
URL: /products/review/
Method: GET
Header: Platform-Header
Request: No Query Params
Response:
{
  "meta": "",
  "data": [
    {
      "image_url": "https://www.facebook.com/img/123",
      "review": "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmo tempor incididunt utnsequat",
      "reviewer": "Rita Singh"
    },
    {
      "image_url": "https://www.facebook.com/img/123",
      "review": "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmo tempor incididunt utnsequat",
      "reviewer": "Rita Singh"
    },
    {
      "image_url": "https://www.facebook.com/img/123",
      "review": "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmo tempor incididunt utnsequat",
      "reviewer": "Rita Singh"
    },
    {
      "image_url": "https://www.facebook.com/img/123",
      "review": "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmo tempor incididunt utnsequat",
      "reviewer": "Rita Singh"
    },
    {
      "image_url": "https://www.facebook.com/img/123",
      "review": "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmo tempor incididunt utnsequat",
      "reviewer": "Rita Singh"
    }
  ]
}
 
 
2.
API Name: School Partnership API
Status: Might not be required, need to be discussed
URL: /products/school_partnership/
Method: GET
Header: Platform-Header
Request: No Query Params
Response:
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
 
3.1
API Name: Contact Us API OLD DESIGN
Status: Need to be discuss the URL
URL: /company/contact/
Method: GET
Header: Platform-Header
Request: No Query Params
Response:
{
  "meta": "",
  "data": {
    "contact_introduction": "Have a query? Reach out to us and we'll respond within 48 working hours. Customer feedback is very valuable to us.We encourage you to share your suggestions and promise to do our best to maximize your experience with us.",
    "address": [
      "CampusConnect Technologies Private limited 105 A Wing 1st floor, Kanara Business Center, Sawali Society, Laxmi Nagar Ghatkopar East, Mumbai – 400075"
  ],
    "email": [
      "support@logiqids.com"
  ],
    "phone": [
    "+ 91 7045345345",
    "+ 91 8080809604"
  ],
    "availablity": "Monday to Friday (10:00 am to 7:00 pm)",
    "twitter": "https://www.twitter.com/logikids",
    "facebook": "https://www.facebook.com/logikids",
    "linkedin": "https://www.linkedin.com/logikids",
    "google": "https://www.google.com/logikids",
    "youtube": "https://www.youtube.com/logikids"
  }
}
 
3.1
API Name: Contact Us API NEW DESIGN
Status: Need to be discuss the URL
URL: /company/contact/
Method: GET
Header: Platform-Header
Request: No Query Params
Response:
{
  "meta": "",
  "data": {
  "contact_info": {
    "name": "Contact Info",
    "address": [
      "Campus Connect Technologies Private limited 105 A Wing 1st floor, Kanara Business Center, Sawali Society, Laxmi Nagar Ghatkopar East, Mumbai – 400075"
    ],
   "email": [
        "support@logiqids.com"
    ],
    "phone": [
      "+ 91 7045345345",
      "+ 91 8080809604"
    ]
  },
  "contact_form": {
    "name": "Get in touch with us",
    "message": [
      "Have a query? Reach out to us and we'll respond within 48 working hours. Customer feedback is very valuable to us.",
      "We encourage you to share your suggestions and promise to do our best to maximize your experience with us."
    ]
  }
  }
}
 
3.2
API Name: Contact Us Post API
Status: Need to be discuss the URL
URL: /company/contact/
Method: POST
Header: Platform-Header
Request:
{
    "name" : "Nimesh Verma",
    "email" : "nimesh.aug11@gmail.com",
  "mobile" : "9911616971",
    "query : "Can I get test package for my 9 month baby?",
    "captcha_valid" : true,
  }
}
Response:
{
    "meta" : "",
    "data" : {
        "message":"Your query has been submitted, We will get back to you ASAP"
  }
}




 
4.
API Name: FAQ API
Status: Need to be discuss the URL
URL: /company/faqs/
Method: GET
Header: Platform-Header
Request: No Query Params
Response:
{
  "meta": "",
  "data": {
    "contact": {
      "contact_introduction": "Have a query? Reach out to us and we'll respond within 48 working hours. Customer feedback is very valuable to us.We encourage you to share your suggestions and promise to do our best to maximize your experience with us.",
      "address": [
        "CampusConnect Technologies Private limited 105 A Wing 1st floor, Kanara Business Center, Sawali Society, Laxmi Nagar Ghatkopar East, Mumbai – 400075"
    ],
      "email": [
        "support@logiqids.com"
    ],
      "phone": [
        "+ 91 7045345345",
        "+ 91 8080809604"
    ],
      "availablity": "Monday to Friday (10:00 am to 7:00 pm)",
      "twitter": "https://www.twitter.com/logikids",
      "facebook": "https://www.facebook.com/logikids",
      "linkedin": "https://www.linkedin.com/logikids",
      "google": "https://www.google.com/logikids",
      "youtube": "https://www.youtube.com/logikids"
  },
    "faqs": [
    {
        "category": "General",
        "data": [
        {
            "question": "What is LogIQids?",
            "answer": "LogIQids is a first of its kind customized tool to enhance the Logical Reasoning skills in kids in the most structured way possible. Logical reasoning is a very important skill-set which is not taught in school. With LogIQids we provide a structured and personalized way to develop this skill in school going children."
        },
        {
            "question": "What is LogIQids?",
            "answer": "LogIQids is a first of its kind customized tool to enhance the Logical Reasoning skills in kids in the most structured way possible. Logical reasoning is a very important skill-set which is not taught in school. With LogIQids we provide a structured and personalized way to develop this skill in school going children."
        },
        {
            "question": "What is LogIQids?",
            "answer": "LogIQids is a first of its kind customized tool to enhance the Logical Reasoning skills in kids in the most structured way possible. Logical reasoning is a very important skill-set which is not taught in school. With LogIQids we provide a structured and personalized way to develop this skill in school going children."
        },
        {
            "question": "What is LogIQids?",
            "answer": "LogIQids is a first of its kind customized tool to enhance the Logical Reasoning skills in kids in the most structured way possible. Logical reasoning is a very important skill-set which is not taught in school. With LogIQids we provide a structured and personalized way to develop this skill in school going children."
        }
      ]
    },
    {
        "category": "Features",
        "data": [
        {
          "question": "What are the key skill-sets LogIQids endeavours to improve?",
            "answer": "The entire Logical Reasoning curriculum has been divided into six different skillsets which are honed and developed over a period of time."
        },
          {
            "question": "What are the key skill-sets LogIQids endeavours to improve?",
            "answer": "The entire Logical Reasoning curriculum has been divided into six different skillsets which are honed and developed over a period of time."
        },
        {
            "question": "What are the key skill-sets LogIQids endeavours to improve?",
            "answer": "The entire Logical Reasoning curriculum has been divided into six different skillsets which are honed and developed over a period of time."
        },
        {
            "question": "What are the key skill-sets LogIQids endeavours to improve?",
            "answer": "The entire Logical Reasoning curriculum has been divided into six different skillsets which are honed and developed over a period of time."
        }
      ]
    },
    {
        "category": "Pricing & Payments",
        "data": [
        {
            "question": "Is the fee refundable?",
            "answer": "100% money back guarantee if you cancel within 15 days of your purchase. After that, there will be no refund of fee. Kindly note that this option is valid only for the Content Subscription only and there should be a minimum of 45 days left before the expiry of the subscription."
        },
        {
            "question": "Is the fee refundable?",
            "answer": "100% money back guarantee if you cancel within 15 days of your purchase. After that, there will be no refund of fee. Kindly note that this option is valid only for the Content Subscription only and there should be a minimum of 45 days left before the expiry of the subscription."
        },
        {
            "question": "Is the fee refundable?",
            "answer": "100% money back guarantee if you cancel within 15 days of your purchase. After that, there will be no refund of fee. Kindly note that this option is valid only for the Content Subscription only and there should be a minimum of 45 days left before the expiry of the subscription."
        },
        {
            "question": "Is the fee refundable?",
            "answer": "100% money back guarantee if you cancel within 15 days of your purchase. After that, there will be no refund of fee. Kindly note that this option is valid only for the Content Subscription only and there should be a minimum of 45 days left before the expiry of the subscription."
        }
      ]
    },
    {
        "category": "For Test",
        "data": [
        {
            "question": "What will happen after I make the booking?",
            "answer": "You will get a welcome email from LogIQids within 2 working days confirming your registration. The email will contain your login details (username and password) and schedule for upload of sample papers (total 4) and topic notes (total 5) to your account."
        },
        {
            "question": "What will happen after I make the booking?",
            "answer": "You will get a welcome email from LogIQids within 2 working days confirming your registration. The email will contain your login details (username and password) and schedule for upload of sample papers (total 4) and topic notes (total 5) to your account."
        },
        {
            "question": "What will happen after I make the booking?",
            "answer": "You will get a welcome email from LogIQids within 2 working days confirming your registration. The email will contain your login details (username and password) and schedule for upload of sample papers (total 4) and topic notes (total 5) to your account."
        },
        {
            "question": "What will happen after I make the booking?",
            "answer": "You will get a welcome email from LogIQids within 2 working days confirming your registration. The email will contain your login details (username and password) and schedule for upload of sample papers (total 4) and topic notes (total 5) to your account."
        }
      ]
    }
  ]
  }
}
 
 
5.
API Name: Capcha API
Status: Need to be discuss the Usage and URL
URL: /utility/captcha/
Method: GET
Header: Platform-Header
Request: No Query Params
Response:
{
  "meta": "",
  "data": {
    "image_url": "https://www.facebook.com/img/123",
    "correct_value": "IVijqer"
  }
}
 



6.
API Name: Pricing API
Status: Need to be discuss the Usage and URL
URL: /product/pricing/
Method: GET
Header: Platform-Header
Request: No Query Params
Response:
{
  "meta": "",
  "data": {
    "message": {
      "heading": "Simple & transparent pricing",
      "bottom": "15-Days, No Questions Asked, Full Money-Back Guarantee. (Valid only for the Content Subscription)"
    },
    "pricing":{
      "features":{
        "name":"Features Given:",
        "data":[
          {
            "id":"1",
            "name": "Topic Notes",
            "description": "Lorem ipsum dolor sit ametconsectetur adipiscing elit sed doeiusmod tempor incidid"
          },
          {
            "id":"2",
            "name": "Adaptive Worksheet",
            "description": "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incidid"
          },
          {
            "id":"3",
            "name": "Skill Based Learning",
            "description": "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incidid"
          },
          {
            "id":"4",
            "name": "In-Depth Analysis",
            "description": "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incidid"
          },
          {
            "id":"5",
            "name": "Progress Review",
            "description": "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incidid"
          },
          {
            "id":"6",
            "name": "First Level Test",
            "description": "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incidid"
          }
        ]
      },
    "plans": [
      {
        "image_url": "https://www.facebook.com/img/123",
        "video_url": "https://www.facebook.com/img/123",
        "name": "Test",
        "price": 550,
        "discount": 0,
        "footnote": "Includes 4 sample papers and 5 Topic Notes",
        "features": {
          "1": true,
          "2": false,
          "3": false,
          "4": true,
          "5": false,
          "6": true
          }
      },
      {
        "image_url": "https://www.facebook.com/img/123",
        "video_url": "https://www.facebook.com/img/123",
        "name": "Content",
        "price":900,
        "discount":0,
        "footnote": "",
        "features": {
          "1": true,
          "2": true,
          "3": true,
          "4": true,
          "5": true,
          "6": false
          }
      },
      {
        "image_url": "https://www.facebook.com/img/123",
        "video_url": "https://www.facebook.com/img/123",
        "name": "Test + Content",
        "discount":0,
        "footnote": "",
        "features": {
          "1": true,
          "2": true,
          "3": true,
          "4": true,
          "5": true,
          "6": true
          }
      }
    ]
  }
}
}


 
 
7.
API Name: City API
Status: Need to be discuss URL
URL: /utility/test/city/
Method: GET
Header: Platform-Header
Request: No Query Params
Response:
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

8.
API Name: Class API
Status: Need to be discuss URL
URL: /user/class/
Method: GET
Header: Platform-Header
Request: No Query Params
Response:
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
 
9.1
API Name: Registration API
Status: Need to be discuss URL
URL: /user/registration/
Method: GET
Header: Platform-Header
Request: queryparams = city_id
Response:
{
  "meta": "",
  "data": {
  "message": {
    "heading": "Tentative test schedule:"
  },
  "test_schedule": [
    {
      "name": "Level 1:",
      "image_url": "https://www.facebook.com/img/123",
      "schedule": "Nov/Dec 2017",
      "footnote": "(Exact date to depend on the centre)"
    },
    {
      "name": "Level 2:",
      "image_url": "https://www.facebook.com/img/123",
      "schedule": "April 2018",
      "footnote": "(Only for eligible candidates)"
    }
  ]
  }
}
 

9.2
API Name: Registration API
Status: Need to be discuss URL
URL: /user/registration/
Method: POST
Header: Platform-Header
Request:
 
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
 
Response:
 {
  "meta": "",
  "data": {
    "customer_id": 101,
    "session_id": "logikids_101_Ad10w9TSOLRlH0tI6clnA8KXchFXd3kl"
  }
}
 
10.
API Name: Test Leads API
Status: Need to be discuss URL
URL: /user/lead/
Method: POST
Header: Platform-Header
Request:
 
{
  "full_name": "Nimesh Kiran Verma",
  "mobile_number":"9911616971",
  "email":"nimesh.aug11@gmail.com",
  "city_id":1,
  "class_id":1,
  "school":"St Xaviers Sr Sec School",
}
 
Response:
{
  "meta": "",
  "data": {
    "sample_test_paper":"Multipart PDF File",
    "message":"Thanks for trying Us"
  
}
 
11.
API Name: Login API
Status: Need to be discuss URL
URL: /user/login/
Method: POST
Header: Platform-Header
Request:
{
  "email":"nimesh.aug11@gmail.com",
  "password":"password123"
}
 
Response:
 
 
 
{
  "meta": "",
  "data": {
    "customer_id": 101,
    "session_id": "logikids_101_Ad10w9TSOLRlH0tI6clnA8KXchFXd3kl"
  }
}
 
 
12.
API Name: Forgot Password API
Status: Need to be discuss URL
URL: /user/forgot_password/
Method: POST
Header: Platform-Header
Request:
{
  "email":"nimesh.aug11@gmail.com",
}
 
Response:
{
  "meta": "",
  "data": {
  "message ":"Password Reset Link has been sent to your registered Email"
  }
}
 
13.1
API Name: Reset Password API
Status: Need to be discuss URL
URL: /user/forgot_password/
Method: GET
Header: Platform-Header
Request: Query Params
id=4675&code=uAm-wlA6HKsuZsZYREZlgfkJzhR7ikG3
 
 
 
 
Response:
{
  "meta": "",
  "data": {
  "email ":"nimesh.aug11@gmail.com"
  }
}
 
13.2
API Name: Reset Password API
Status: Need to be discuss URL
URL: /user/forgot_password/
Method: POST
Header: Platform-Header
Request:
{
  "id": "4675",
  "code": "uAm-wlA6HKsuZsZYREZlgfkJzhR7ikG3",
  "email ":nimesh.aug11@gmail.com,
  "password":"new_password"
}
 
 
 
 
Response:
{
  "meta": "",
  "data": {
  "email ":"nimesh.aug11@gmail.com"
  }
}
 






























Loggedin APIs

14.1
API Name: Profile API
Status: Need to be discuss URL
URL: /user/profile/
Method: POST
Header: Loggedin-Platform-Header
Request:
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
Response:
{
  "meta": "",
  "data": {
    "customer_id": 123,
    "full_name": "Nimesh Kiran Verma",
    "mobile_number": "9911616971",
    "email": "nimesh.aug11@gmail.com",
    "city_id": 1,
    "class_id": 1,
    "school": "St Xaviers Sr Sec School",
    "profile_pic": "https://9gag.com/gag/a5nEdzg"
  }
}

14.2
API Name: Profile API
Status: Need to be discuss URL
URL: /user/123/profile/
Method: GET
Header: Loggedin-Platform-Header
Request: Query Params None
Response:
{
  "meta": "",
  "data": {
    "customer_id": 123,
    "full_name": "Nimesh Kiran Verma",
    "mobile_number": "9911616971",
    "email": "nimesh.aug11@gmail.com",
    "city_id": 1,
    "class_id": 1,
    "school": "St Xaviers Sr Sec School",
    "profile_pic": "https://9gag.com/gag/a5nEdzg"
  }
}

14.3
API Name: Profile API
Status: Need to be discuss URL
URL: /user/123/profile/
Method: PUT
Header: Loggedin-Platform-Header
Request:
{
  "full_name": "Nimesh Kiran Verma",
  "mobile_number": "9911616971",
  "email": "nimesh.aug11@gmail.com",
  "city_id": 1,
  "class_id": 1,
  "school": "St Xaviers Sr Sec School",
  "profile_pic": "https://9gag.com/gag/a5nEdzg"
}
Response:
{
  "meta": "",
  "data": {
    "customer_id": 123,
    "full_name": "Nimesh Kiran Verma",
    "mobile_number": "9911616971",
    "email": "nimesh.aug11@gmail.com",
    "city_id": 1,
    "class_id": 1,
    "school": "St Xaviers Sr Sec School",
    "profile_pic": "https://9gag.com/gag/a5nEdzg"
  }
}
15
API Name: Change Password API
Status: Need to be discuss URL
URL: /user/123/password/
Method: Post
Header: Loggedin-Platform-Header
Request: 
{
    "customer_id": 123,
    "old_password": "pass123",
    "new_password": "newpass123"
  }
Response:
{
  "meta": "",
  "data": {}
}
16
API Name: Order API
Status: Need to be discuss URL
URL: /user/123/orders/
Method: Post
Header: Loggedin-Platform-Header
Request: None
Response:
{
  "meta": "",
  "data": {
    "orders": [
      {
        "order_no": "1",
        "amount": 1444,
        "details": "jvckdjsjvaxncs x",
        "date": "20/11/2017"
      },
      {
        "order_no": "1",
        "amount": 1444,
        "details": "jvckdjsjvaxncs x",
        "date": "20/11/2017"
      },
      {
        "order_no": "1",
        "amount": 1444,
        "details": "jvckdjsjvaxncs x",
        "date": "20/11/2017"
      },
      {
        "order_no": "1",
        "amount": 1444,
        "details": "jvckdjsjvaxncs x",
        "date": "20/11/2017"
      },
      {
        "order_no": "1",
        "amount": 1444,
        "details": "jvckdjsjvaxncs x",
        "date": "20/11/2017"
      }
    ]
  }
}

15.1
API Name: Refer API
Status: Need to be discuss URL
URL: /user/123/refer/
Method: GET
Header: Loggedin-Platform-Header
Request: Query Params None
Response:
{
  "meta": "",
  "data": {
    "wallet": {
      "balance": 0
    },
    "refer_message": {
      "whatsapp": "whatsapp://send?text=Hi - wanted to share this very interesting Logical Reasoning Competition designed by IIT-IIM alumni, to initiate kids into logical thinking.  I think it provides a great exposure to kids. %0aThe exam is designed to stimulate the analytical thinking in kids and is conducted for SrKG to Class 9 kids. For Sr KG and Grade 1 kids, their invigilators read and explain the question to kids.%0aYou could DOWNLOAD a FREE SAMPLE PAPER from the link below: https://www.logiqids.com/user/register?c=Nimesh773",
      "facebook": "https://www.facebook.com/v2.3/dialog/feed?app_id=1855999688021475&caption=Logiqids.com&description=%20Download%20Free%20Sample%20Paper%20for%20LogIQids%20Logical%20Reasoning%20Exam%20.&link=https://www.logiqids.com/user/register?c=Nimesh773&name=Must%20Try%20For%20Parents%20of%205%20to%2012%20Year%20Old%20Children!&picture=https://www.logiqids.com/images/LogIQids_FB_final1.png",
      "sms": "sms:?body=Hi - wanted to share this very interesting Logical Reasoning Competition designed by IIT-IIM alumni, to initiate kids into logical thinking.  I think it provides a great exposure to kids. %0aThe exam is designed to stimulate the analytical thinking in kids and is conducted for SrKG to Class 9 kids. For Sr KG and Grade 1 kids, their invigilators read and explain the question to kids.%0aYou could DOWNLOAD a FREE SAMPLE PAPER from the link below: https://www.logiqids.com/user/register?c=Nimesh773"
    }
  }
}


Note : Take a Tour Via JSON

16.1
API Name: Ask A Query API
Status: Need to be discuss URL
URL: /user/123/refer/
Method: GET
Header: Loggedin-Platform-Header
Request: Query Params None
Response:
{
  "meta": "",
  "data": {
    "full_name": "Nimesh Kiran Verma",
    "mobile_number": "9911616971",
    "email": "nimesh.aug11@gmail.com"
  }
}








16.2
API Name: Ask A Query API
Status: Need to be discuss URL
URL: /user/123/refer/
Method: GET
Header: Loggedin-Platform-Header
Request: 
{
  "meta": "",
  "data": {
    "full_name": "Nimesh Kiran Verma",
    "mobile_number": "9911616971",
    "email": "nimesh.aug11@gmail.com",
    "category_id": 1,
    "query":"Please Help" ,
   "file_link": "https://9gag.com/gag/a5nEdzg"

  }
}

Response:
{
  "meta": "",
  "data": {
    "message": "We will get back to you."
  }
}


16.2
API Name: User Product APIs
Status: Need to be discuss URL
URL: /user/123/products/
Method: GET
Header: Loggedin-Platform-Header
Request: 

Response:
{
  "meta": "",
  "data": {
    "products": {
      "test": [
        {
          "id": 123,
          "name": "Mumbai 23 Dec Test",
          "subscription_date": "dd/mm/yyyy",
          "active": true
        },
        {
          "id": 124,
          "name": "Mumbai 29 Dec Test",
          "subscription_date": "dd/mm/yyyy",
          "active": false
        }
      ],
      "content": [
        {
          "id": 123,
          "name": "Annual Content",
          "subscription_date": "dd/mm/yyyy"
        },
        {
          "id": 124,
          "name": "Summer Content",
          "subscription_date": "dd/mm/yyyy",
          "active": false
        }
      ]
    }
  }
}


17.
API Name: Mega Menu
Status: Need to be discuss URL
URL: /user/id/menu
Method: GET
Header: Loggedin-Platform-Header
Request:
Response:
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


 

17
API Name: Test subscription
Status: Need to be discuss URL
URL: /product/test/
Method: GET
Header: Platform-Header
Request:
Response:
{
  "meta": "",
  "data": {
  "sample_paper": "https://www.facebook.com/img/123",
  "test_data": [
    {
      "city_id": 1,
      "city": "Mumbai",
      "price": 550,
      "package_id": 123,
      "message": [
        "Level 1: Scheduled in Nov - Dec 2017 (Exact date to depend on the centre)",
        "Level 2: Scheduled in April 2018 (only for eligible candidates)"
      ]
    },
    {
      "city_id": 2,
      "city": "Ahemdabad",
      "price": 550,
      "package_id": 124,
      "message": [
        "Level 1: Scheduled in Nov - Dec 2017 (Exact date to depend on the centre)",
        "Level 2: Scheduled in April 2018 (only for eligible candidates)"
      ]
    },
    {
      "city_id": 3,
      "city": "Pune",
      "price": 550,
      "package_id": 125,
      "message": [
        "Level 1: Scheduled in Nov - Dec 2017 (Exact date to depend on the centre)",
        "Level 2: Scheduled in April 2018 (only for eligible candidates)"
      ]
    },
    {
      "city_id": 4,
      "city": "Delhi",
      "price": 550,
      "package_id": 125,
      "message": [
        "Level 1: Scheduled in Nov - Dec 2017 (Exact date to depend on the centre)",
        "Level 2: Scheduled in April 2018 (only for eligible candidates)"
      ]
    }
  ]
  }
}
 
18
API Name: Order Review API
Status: Need to be discuss URL
URL: /user/123/order/review/
Method: POST
Header: Loggedin-Platform-Header
Request:
{
  "package_ids": [
  23,
  24
  ],
  "test": true,
  "content": true
}
Response:
{
  "meta": "",
  "data": {
    
    "package_data": [
      {
        "id": 23,
        "name": "LogIQids Logical Reasoning Exam",
        "class_name": "Class 5",
        "academic_session": "2017-18",
        "info": "Mumbai",
        "price": 550
      },
      {
        "id": 24,
        "name": "Content Package",
        "class_name": "Class 5",
        "academic_session": "2017-18",
        "info": "Package Valid upto Dec 31 2017",
        "price": 900
      }
    ]
  }
}

 

19
API Name: Payment Details API
Status: Need to be discuss URL
URL: /user/123/payment_details/
Method: POST
Header: Loggedin-Platform-Header
Request:
{
  "order_id": 123
  "state_id": 1
}
Response:
{
  "meta": "",
  "data": {
    "order_id": 1,
    "amount": 1212
  }
}

20
API Name: Weekly leaderboard API
Status: Need to be discuss URL
URL: /results/toppers/weekly/
Method: GET
Header: Loggedin-Platform-Header
Request:None
Response:
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

21
API Name: Topic Notes API
Status: Need to be discuss URL
URL: /test/topic_notes/
Method: POST
Header: Loggedin-Platform-Header
Request: None
Response:
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
22
API Name: Current Test Schedule API
Status: Need to be discuss URL
URL: /test/scheduel/
Method: POST
Header: Loggedin-Platform-Header
Request: None
Response:
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
23
API Name: Sample Paper Status API
Status: Need to be discuss URL
URL: /test/sample_paper/status/
Method: POST
Header: Loggedin-Platform-Header
Request: None
Response:
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


pic_a


pic_b


pic_c


pic_d

24
API Name: Sample Paper Download API
Status: Need to be discuss URL
URL: /test/sample_paper/<sample_paper_id>/
Method: POST
Header: Loggedin-Platform-Header
Request: None
Response:
{
  "meta": "",
  "data": {
// Multipart form
}
}

25
API Name: Sample Paper Solutions Download API
Status: Need to be discuss URL
URL: /test/sample_paper/<sample_paper_id>/solutions/
Method: POST
Header: Loggedin-Platform-Header
Request: None
Response:
{
  "meta": "",
  "data": {
// Multipart form
}
}

26
API Name: Sample Paper Answers Submit API
Status: Need to be discuss URL
URL: /test/sample_paper/<sample_paper_id>/answers/
Method: POST
Header: Loggedin-Platform-Header
Request: 
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

Response:
{
  "meta": "",
  "data": {}
}

25.2
API Name: Sample Paper Answers Submit API
Status: Need to be discuss URL
URL: /test/sample_paper/<sample_paper_id>/answers/
Method: GET
Header: Loggedin-Platform-Header
Request: None
Response:
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
27
API Name: Sample Paper Attempt complete API
Status: Need to be discuss URL
URL: /test/sample_paper/<sample_paper_id>/attempt/
Method: POST
Header: Loggedin-Platform-Header
Request: None
Response:
{
  "meta": "",
  "data": {
}
}

28.1
API Name: Sample Paper Question API
Status: Need to be discuss URL
URL: /test/sample_paper/<sample_paper_id>/question/<question_id>/
Method: GET
Header: Loggedin-Platform-Header
Request: None
Response:
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

29
API Name: Sample Paper Question Answer API
Status: Need to be discuss URL
URL: /test/sample_paper/<sample_paper_id>/question/<question_id>/answer
Method: POST
Header: Loggedin-Platform-Header
Request: {
  "answer_id":"a"
}
Response:
{
  "meta": "",
  "data": {}
}

30
API Name: Sample Paper Analysis API
Status: Need to be discuss URL
URL: /test/sample_paper/<sample_paper_id>/analysis/
Method: POST
Header: Loggedin-Platform-Header
Request: None
Response:
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



31
API Name: Sample Paper Analysis API
Status: Need to be discuss URL
URL: /test/sample_paper/analysis/
Method: POST
Header: Loggedin-Platform-Header
Request: None
Response:
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
API Name: Past Test Analysis API
Status: Need to be discuss URL
URL: /test/past/analysis/
Method: POST
Header: Loggedin-Platform-Header
Request: None
Response:
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
API Name: Past Test Detailed Analysis API
Status: Need to be discuss URL
URL: /test/<test_id>/analysis/
Method: POST
Header: Loggedin-Platform-Header
Request: None
Response:
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
API Name: Sample Paper Analysis API
Status: Need to be discuss URL
URL: /content/package_subscribed/<package_subscribtion_id>/analysis/
Method: POST
Header: Loggedin-Platform-Header
Request: None
Response:
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
API Name: Topic API
Status: Need to be discuss URL
URL: /content/topics/
Method: POST
Header: Loggedin-Platform-Header
Request: None
Response:
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
API Name:Topic worksheet Status API
Status: Need to be discuss URL
URL: /content/topic/<topic_id>/worksheet/
Method: POST
Header: Loggedin-Platform-Header
Request: None
Response:
{
  "meta": "",
  "data": {
          "id":123,
          "online_test": "not_started/started/completed",
          "offline_test": "not_started/started/completed"
  }
}


35
API Name:Topic worksheet Status API
Status: Need to be discuss URL
URL: /content/topic/<topic_id>/worksheet/
Method: POST
Header: Loggedin-Platform-Header
Request: None
Response:
{
  "meta": "",
  "data": {
          "id":123,
          "online_test": "not_started/started/completed",
          "offline_test": "not_started/started/completed"
  }
}

36
API Name: Sample Paper Analysis API
Status: Need to be discuss URL
URL: /test/sample_paper/analysis/
Method: POST
Header: Loggedin-Platform-Header
Request: None
Response:
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
API Name: Topic Notes API
Status: Need to be discuss URL
URL: /test/topic/<topic_id>/notes/
Method: POST
Header: Loggedin-Platform-Header
Request: None
Response:
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
API Name: Topic Past worksheet API
Status: Need to be discuss URL
URL: /test/topic/past_worksheet/
Method: POST
Header: Loggedin-Platform-Header
Request: None
Response:
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
API Name: Topic Past worksheet API
Status: Need to be discuss URL
URL: /test/topic/<topic_id>/past_worksheet/
Method: POST
Header: Loggedin-Platform-Header
Request: None
Response:
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
API Name: Worksheet Download API
Status: Need to be discuss URL
URL: /content/topic/<topic_id>/worksheet/<worksheet_id>
worksheet_id can be latest
Method: POST
Header: Loggedin-Platform-Header
Request: None
Response:
{
  "meta": "",
  "data": {
// Multipart form
}
}

40
API Name: Worksheet Solutions Download API
Status: Need to be discuss URL
URL: /content/topic/<topic_id>/worksheet/<worksheet_id>/solutions/
worksheet_id can be latest
Method: POST
Header: Loggedin-Platform-Header
Request: None
Response:
{
  "meta": "",
  "data": {
// Multipart form
}
}

41.1
API Name: Worksheet Answers Submit API
Status: Need to be discuss URL
URL: /content/topic/<topic_id>/answers/
Method: POST
Header: Loggedin-Platform-Header
Request: 
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

Response:
{
  "meta": "",
  "data": {

    "heading": "Topic : Puzzles Worksheet Download Date : 11-Jul-2017",
    "result": [{
        "name": "Question Asked",
        "value": 15
      },
      {
        "name": "Attempted",
        "value": 1
      },
      {
        "name": "Correct",
        "value": 0
      },
      {
        "name": "Score",
        "value": 0
      }

    ]

  }
}


41.2
API Name: Worksheet Answers Submit API
Status: Need to be discuss URL
URL:  /content/topic/<topic_id>/worksheet/<worksheet_id>/solutions/
Method: GET
Header: Loggedin-Platform-Header
Request: None
Response:
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

43
API Name: Worksheet Attempt complete API
Status: Need to be discuss URL
URL:  /content/topic/<topic_id>/worksheet/<worksheet_id>/attempt/
worksheet_id can be latest
Method: POST
Header: Loggedin-Platform-Header
Request: None
Response:
{
  "meta": "",
  "data": {
}
}

44
API Name: Worksheet Question API
Status: Need to be discuss URL
URL: /content/topic/<topic_id>/worksheet/<worksheet_id>/question/<question_id>/
Method: GET
Header: Loggedin-Platform-Header
Request: None
Response:
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

45
API Name: Worksheet Question Answer API
Status: Need to be discuss URL
URL: /content/topic/<topic_id>/worksheet/<worksheet_id>/question/<question_id>/answer
Method: POST
Header: Loggedin-Platform-Header
Request: {
  "answer_id":"a"
}
Response:
{
  "meta": "",
  "data": {}
}

46
API Name: Worksheet Analysis API
Status: Need to be discuss URL
URL:/content/topic/<topic_id>/worksheet/<worksheet_id>/analysis/
Method: POST
Header: Loggedin-Platform-Header
Request: None
Response:
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





