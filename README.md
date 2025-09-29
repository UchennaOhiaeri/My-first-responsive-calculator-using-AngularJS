# My-Calculator-App
This is a simple AngularJS calculator project I built to practice `ng-app`, `ng-model`, `ng-click`, and `ng-controller`.




<!DOCTYPE html>
<html lang="en" ng-app="calcApp">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Responsive AngularJS Calculator</title>
  <script src="angular-1.5.0/angular.min.js"></script>
  <link src="stylesheet" href="design.css">
  <style>
    * {
      box-sizing: border-box;
    }
    body {
      font-family: Arial, sans-serif;
      display: flex;
      justify-content: center;
      align-items: center;
      min-height: 100vh;
      margin: 0;
      padding: 10px;
    }
    .container {
      border: 3px solid black;
      padding: 20px;
      max-width: 500px;
      width: 100%;
    }
    .row {
      margin-bottom: 15px;
    }
    label {
      display: inline-block;
      width: 100px;
      font-weight: bold;
    }
    input {
      width: calc(100% - 110px);
      padding: 8px;
      border: 2px solid black;
      font-size: 16px;
    }
    .buttons {
      display: flex;
      justify-content: space-between;
      flex-wrap: wrap;
      margin-top: 15px;
    }
    button {
      flex: 1 1 22%;
      padding: 10px;
      margin: 5px;
      border: 2px solid black;
      font-size: 16px;
      font-weight: bold;
      background: white;
      cursor: pointer;
    }
    .answer {
      margin-top: 20px;
      font-size: 18px;
      font-weight: bold;
    }

    
    @media (max-width: 500px) {
      label {
        width: 100%;
        margin-bottom: 5px;
      }
      input {
        width: 100%;
      }
    }
  </style>
</head>
<body ng-controller="CalcController">
  <div class="container">
    <div class="row">
      <label for="firstnum">FIRSTNUM</label>
      <input type="number" id="firstnum" ng-model="firstnum">
    </div>
    <div class="row">
      <label for="secondnum">SECONDNUM</label>
      <input type="number" id="secondnum" ng-model="secondnum">
    </div>
    <div class="buttons">
      <button ng-click="add()">ADD</button>
      <button ng-click="sub()">SUB</button>
      <button ng-click="mul()">MUL</button>
      <button ng-click="div()">DIV</button>
    </div>
    <div class="answer">The answer is: {{result}}</div>
  </div>

  <script>
    angular.module('calcApp', [])
      .controller('CalcController', ['$scope', function($scope) {
        $scope.result = "";

        $scope.add = function() {
          $scope.result = Number($scope.firstnum || 0) + Number($scope.secondnum || 0);
        };
        $scope.sub = function() {
          $scope.result = Number($scope.firstnum || 0) - Number($scope.secondnum || 0);
        };
        $scope.mul = function() {
          $scope.result = Number($scope.firstnum || 0) * Number($scope.secondnum || 0);
        };
        $scope.div = function() {
          if ($scope.secondnum == 0) {
            $scope.result = "Cannot divide by zero";
          } else {
            $scope.result = Number($scope.firstnum || 0) / Number($scope.secondnum || 0);
          }
        };
      }]);
  </script>
</body>
</html>
