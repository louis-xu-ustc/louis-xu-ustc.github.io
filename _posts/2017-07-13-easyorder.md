---
layout: post
title: "Easy Order"
---

A mobile application (both Android and IOS) that allows retailer to post their daily dish menu and
customers to order dish and track their order.

#### Project Idea

The project idea comes from Chinese students' CMU life experience.
There are several Chinese restaurants in Pittsburgh that provide take away services, but we have to join their Wechat group in 
order to know daily menu and order information. 
Sometimes, you’ll miss your meal since you’re too busy to check the group notification.

#### Project Features

This app will benefit both the restaurant owner (retailer) and user (customer). 
1. Post Tab: Retailers are able to update their daily menu through this post tab, and the system will help to calculate 
ordered quantity for each dish. Customers can learn dish details through this tab and take their orders and also share the 
message to Twitter.
2. Map(tracking) Tab: customers can track the delivery and the system will notify the user if the delivery is approaching.
3. Payment Tab: retailer can send manual notifications to customers if they forget to fetch their order.
At the same time, customers can pay for their order through the Vemo payment system.

#### Project Techniques
- Twitter
    - (iOS) REST API &  (android) twitter4j library, OAuth 2.0 authentication.
    - users are logged into their twitter account to start using this app
    - users can update status API to share the dish together with its picture on Twitter.
- Google Map API
    - Retailer could set his target goal, and this tab would draw the direction by driving on the map through Google Directions API 
    (search direction, draw direction on map). 
    - Retailer broadcast his real-time position by posting that information into our web service.
- Venmo REST API
    - Retailers’ payment account is pre-configured as part of the application. When the customers confirm paying, payment directly goes into the retailer’s accounts.
- Django Web Server
    - the web server is held on AWS together with a SQL database.
    - The web server would use Django framework to communicate with database and serve our application with Django REST framework 
    - REST APIs provided by our web server public so that we do not need to spend time providing API key generation and registration interface
    - The information we would save in our database include:
        - Dish ordering information (which user order how many serves of which dish, whether this transaction is payed)
        - Dish detail information (image URL of dish, its name, and optionally its rating) (We would consider serve those images as static files in our web server)
        - Retailer Location (latitude and longitude)
        - Notifications (pick up order)


![Easy Order Architecture](/images/20170713/easyOrderArchitecture.png){:height="50%" width="50%"}{: .center-image }
***Figure 1.** Easy Order Application Architecture*

[![A short video to introduce easy order application](/images/20170713/easyOrderLogin.png){:height="40%" width="40%"}{: .center-image }](TBD)
***Video 1.** A short video that introduce easy order application [To be added]*

#### More details:  
[Github: Easy Order Android](https://github.com/louis-xu-ustc/EasyOrder_Android)  
[Github: Easy Order IOS](https://github.com/louis-xu-ustc/EasyOrder_IOS)  
[Github: Easy Order Backend](https://github.com/louis-xu-ustc/EasyOrder_Backend)  


