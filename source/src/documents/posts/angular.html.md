---
layout: 'content'
title: 'AngularJS'
description: ''
---
# Install

# Khởi tạo template

Template

```
<html ng-app="phonecatApp">
<head>
    <script src="bower_components/angular/angular.js"></script>
    <script src="js/controllers.js"></script>
</head>
<body ng-controller="PhoneListCtrl">
    
</body>
</html>
```

Controller, controllers.js

```
var phonecatApp = angular.module('phonecatApp',[]);
phonecatApp.controller('PhoneListCtrl', function($scope){
    $scope.phones = '...';
    })
```

# Print giá trị trả về

```
{{ phones | json }}
```

# Lấy 5 đối tượng đầu tiên từ json trả về


```
$scope.phones = data.splice(0,5);
```


# Lấy dữ liệu từ server

```
phonecatApp.controller('PhoneListCtrl',function($scope, $http){
    $http.get('phones/phones.json').success(function(data) {
        $scope.phones = data;
      });
    })
```

# Filter data

Template

```
<input type="text" ng-model="query">
<li ng-repeat="phone in phones | filter:query">
</li>
```

# Order

controller

```
$scope.orderProp = 'age';
```

template

```
<select ng-model="orderProp">
    <option value="name">Alpha</option>
    <option value="age">Newest</option>
</select>
<li ng-repeat="phone in phones| orderBy:orderProp">
</li>
```

# Chèn hình

```
<img ng-src="{{phone.imageUrl}}" alt="">
```

# Built link

```
<a href="#/phones/{{phone.id}}"></a>
```

# Routing

Thêm vào bower.json
"angular-route": "~1.2.x"

Template

```
<script src="bower_components/angular-route/angular-route.js"></script>
<script src="bower_components/angular-route/app.js"></script>

<div ng-view></div>
```