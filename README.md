# read-angularJs-edits-form-
The form validation code is a angularJS beginners
<!DOCTYPE html>
<html ng-app="lesson" >
	<head>
	<meta http-equiv="Content-Type" content="text/html;charset=utf-8">
		<title>Lesson8</title>
		<link rel="stylesheet" type="text/css" href="css/main.css"/>
		<style type="text/css">
			#content{padding:16px;}
		
			#btn ul li{ list-style:none;margin-top:10px;}
		</style>
	</head>
	<body>
		<form name="myForm" ng-submit="PostForm()" ng-controller="FormCtrl" id="btn">
			<ul>
				<li>
					<label>用户名:</label><input type="text" name="UserName1" ng-model="UserName1" ng-pattern="/^\w{8,18}$/" required/>
					<span style="color:red" ng-show="myForm.UserName1.$dirty&&myForm.UserName1.$invalid"><!--$dirty 关键字意思在于输入框中有输入过字符的痕迹，$invalid关键字意思是不合法的输入内容-->
					<span ng-show="myForm.UserName1.$error.required">请输入用户名</span><!--当错误$error触发required事件的时候出现-->
						<span>请输入8到18位的用户名</span>
					</span>
				</li>
				<li>
				
					<label>编号：</label><input type="text" name="UserIndex" ng-model="UserIndex" ng-pattern="/^\d+$/"/><!-- ng-pattern为正则表达式-->
					<span style="color:red" ng-show="myForm.UserIndex.$dirty&&myForm.UserIndex.$invalid">
						请输入您的数字编号
					</span>
				</li>
				<li>
					<label>邮箱:</label><input type="text" name="Email" ng-model="Email" ng-pattern="/^[a-z0-9]+([._\\-]*[a-z0-9])*@([a-z0-9]+[-a-z0-9]*[a-z0-9]+.){1,63}[a-z0-9]+$/" />
					<span style="color:red" ng-show="myForm.Email.$dirty&&myForm.Email.$invalid"><!--$dirty 关键字意思在于输入框中有输入过字符的痕迹，$invalid关键字意思是不合法的输入内容-->
						请输入正确的邮箱
					</span>
				</li>
				<li>
					<input ng-disabled="myForm.$invalid" type="submit" value="提交"/>
				</li>
			</ul>
		</form>
		<script src="scripts/angular-1.0.1.min.js"></script>
		<script>
			var app=angular.module("lesson",[]);
				app.controller("FormCtrl",function($scope){
					$scope.myForm={};
					$scope.UserName1='Tom';
					$scope.PostForm=function(){
						console.log($scope.myForm);
					}
				});
		</script>
	</body>
</html>
