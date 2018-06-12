
<!DOCTYPE html>
<html xmlns:ng="http://angularjs.org" id="ng-app">

<head>

    <meta http-equiv="Content-Type" content="text/html; charset=utf-8"/>
    <link rel="icon" type="image/gif" href="/pages/themesv2/images/favicon.ico">
    <title>Paytm</title>

    <link href="/pages/themesv2/css/angular-material.min.css" rel="stylesheet" type="text/css"/>
    <link href="/pages/themesv2/css/mp-web.min.css?ver=1528794489924" rel="stylesheet" type="text/css"/>

    <meta name="viewport" content="width=device-width, initial-scale=1">


</head>

<!--[if lt IE 9]><script src="java/es5-shim.min.js"></script><![endif]-->

<body>

<!--[if lt IE 10]>
<style>
    md-input-container{
        display: table;
        width: 100%;
    }
    md-input-container input {
        width: inherit;
    }
    .number-prefix-new {
        position: absolute;
        font-size: 14px;
        left: 10px;
        top: 26px;
    }
</style>
<![endif]-->

<!-- Google Tag Manager -->
<noscript><iframe src="//www.googletagmanager.com/ns.html?id=GTM-PTT2P2"
                  height="0" width="0" style="display:none;visibility:hidden"></iframe></noscript>
<script>(function(w,d,s,l,i){w[l]=w[l]||[];w[l].push({'gtm.start':
        new Date().getTime(),event:'gtm.js'});var f=d.getElementsByTagName(s)[0],
        j=d.createElement(s),dl=l!='dataLayer'?'&l='+l:'';j.async=true;j.src=
        '//www.googletagmanager.com/gtm.js?id='+i+dl;f.parentNode.insertBefore(j,f);
})(window,document,'script','dataLayer','GTM-PTT2P2');</script>
<!-- End Google Tag Manager -->
<div id="main-container" ng-view ng-init="subTheme = 'mp-web'; authState = 'f6544170-2014-53aa-95ce-56325668d42f';
    qrLogin = 'true'; qrNodeServerUrl = 'https://accounts-service.paytm.com'; minKycState = 'null'; isKycDocMandate = 'null' ; pubKey = 'null'; min_kyc_redirect_uri = 'null'" ng-class="{'mp-web-main-container clearfix main-container-box': subTheme == 'mp-web' || subTheme == 'mp-mall' || subTheme == 'panel'}">

</div>

<script type="text/template" id="current-form" data-type="login">
    <!--TODO: fix this-->
<div class='login-wrapper'>

        <div ng-init="isSignup = true" >
            <header-strip ng-hide="showNewHeader" sub-theme="{{subTheme}}" header="header" top-righttext="{{isSignup === false ? '' : text.signupLink}}" top-rightfn="callSignUp"></header-strip>
        </div>

        <div class="header-text-wrapper" ng-show="troubleLoggginContainer && showNewHeader && (subTheme == 'mp-html5' || subTheme == 'mall-html5')">
            <span class="header-text">Help me Login</span>
            <span class="signup">
            <a href="" ng-click="helpMeLogin()">Login</a>
        </span>
        </div>

<div id="wallet-container-new" ng-show="showWalletContainer && (subTheme == 'mp-web' || subTheme == 'mp-mall' || subTheme == 'panel' || subTheme == 'sellerpanel')">
    <left-static-section ng-if="subTheme != 'mp-web'"></left-static-section>
    <left-static-section ng-if="((qrLogin == 'null' || qrLogin == 'false')) && subTheme == 'mp-web'"></left-static-section>
    <qr-code-login ng-if="qrLogin == 'true' && subTheme == 'mp-web'"></qr-code-login>
</div>

        <div id="login-header-wrapper" ng-if="subTheme == 'ump' && !trubleLoggin && isIvrFlow">
                    <div id="img-container" ng-if="showImage">
                        <img src="/pages/themesv2/images/paytm-logo.png">
                    </div>
        </div>

        <div id="login-container" ng-show="trubleLoggin" ng-init="sessionData = {
            email : '',
            clientid : 'paytm-web-secure',
            scope : 'paytm',
            response_type : 'code',
            redirect_uri : 'https://paytm.com/v1/api/authresponse',
            state :'null',
            isVerificationExcluded :false,
            theme : 'mp-web',
            errorMsg : '',
            registerRedirectParams : 'client_id=paytm-web-secure&scope=paytm&response_type=code&redirect_uri=https://paytm.com/v1/api/authresponse&theme=mp-web&state=null&is_verification_excluded=false&isSignup=true',
            actionUri : '/oauth2/authorize',
            authState : 'f6544170-2014-53aa-95ce-56325668d42f',
            socialType : 'null',
            isInvalidUserNamePassword :null,
            errorMessage : 'null',
            otpLoginState : '',
            loginMessage : 'One Time Password(OTP) has been sent to your mobile, please enter it here to verify your mobile.',
            minKycMandate : 'null'
            }">

        <div id="login-header-wrapper" ng-if="subTheme != 'mp-html5' && subTheme != 'mall-html5' && subTheme != 'diy' && subTheme != 'dashboard' && subTheme != 'diy-ppb' && subTheme != 'netbanking'">
            <div id="img-container" ng-if="showImage">
                <img src="/pages/themesv2/images/paytm-logo.png">
            </div>

        <ul class="tabs" ng-class="{'mp-web-new' :subTheme == 'mp-web' || subTheme == 'mp-mall' || subTheme == 'scanandpay' || subTheme != 'dashboard' || subTheme != 'diy-ppb'|| subTheme == 'diy' || subTheme == 'panel' || subTheme == 'netbanking'}"
            ng-init="isSignup = true">
            <li class="selected" ng-bind="text.loginLink"></li>
            <li ng-if="isSignup == true" ng-click="callSignUp()" ng-bind="text.signupLink"></li>
        </ul>
    </div>
    <div ng-if="subTheme == 'sellerpanel'"><p class="authenticateHeadingText">Proceed to authenticate</p></div>
    <logo-header ng-if="subTheme == 'diy'" image-name="paytm-logo.png" header-text="Payment Business Login"></logo-header>
    <logo-header ng-if="subTheme == 'dashboard'" image-name="paytmBusiness.svg"></logo-header>
        <div class="netbanking-panel-header" ng-show="subTheme == 'netbanking'">
          <!-- <p class="header dark-blue">India&#39;s most sincere</p>
          <p class="header blue">Bank is here!</p> -->
          <p class="form-header dark-blue">Login to your banking account</p>
        </div>
        <p ng-if="subTheme == 'dashboard'" class="dashboard-login-form-header">Login using your existing Paytm account</p>
            <div class="form-container">
                <form method="post" id="loginForm" name="loginForm"
                      novalidate="novalidate" autocomplete="off" ng-submit="submitLoginForm()">

            <div ng-if="subTheme == 'mp-web'|| subTheme == 'mp-mall' || subTheme == 'scanandpay' || subTheme == 'diy' || subTheme == 'mp-html5' || subTheme == 'mall-html5' || subTheme == 'panel' || subTheme == 'netbanking' || subTheme == 'dashboard' || subTheme == 'diy-ppb'">
                <!-- Fake fields are a workaround for chrome autofill getting the wrong fields -->
                <input style="display:none" type="text" name="fakeusernameremembered"/>
                <input style="display:none" type="password" name="fakepasswordremembered"/>
                <!-- Fake fields end-->

                        <md-content layout-padding="">
                            <md-input-container ng-if="subTheme == 'panel'">
                                <label ng-bind="text.mobileInputLabel"></label>

                                <input type="text" name="username"
                                       ng-model="sessionData.email" autofill-input data-required email-validate
                                       ga-blurevent maxlength="199" data-ng-trim="false"
                                       placeholder="Enter your Email">

                                <div ng-messages="loginForm.username.$dirty">
                                                <span ng-show="loginForm.username.$dirty || showRequired">
                                                <span class="error" ng-show="loginForm.username.$error.required">Email is required.</span>
                                                <span class="error"
                                                      ng-show="loginForm.username.$error.emailValid">Email
                                                    incorrect.
                                                </span>
                                                </span>

                                    <span class="error" ng-show="formError" ng-bind="formErrorMsg"></span>
                                    <!-- Error message from backend -->
                                    <span class="error"
                                          ng-show="sessionData.isInvalidUserNamePassword && !showRequired"
                                          ng-bind="sessionData.errorMessage"></span>
                                </div>

                            </md-input-container>

                            <md-input-container ng-if="(subTheme != 'panel' && subTheme != 'scanandpay') && !(sessionData.minKycMandate == 'true')">
                                <label ng-bind="text.mobileInputLabel"></label>

                                <a class="clearMobileInput"
                                   ng-show="(subTheme == 'mp-html5' || subTheme == 'mall-html5') && sessionData.email && showCrossIcon"
                                   ng-click="sessionData.email = ''">
                                    <img src="/pages/themesv2/images/mp-html5/cross.svg">
                                </a>

                            <input type="text" name="username"
                                    ng-class="{'number-new': ((sessionData.email | isMobile) && loginForm.username.$dirty && !loginForm.username.$error.required)}"
                                    ng-model="sessionData.email" autofill-input data-required email-validate mobile-validate
                                    maxlength="199" data-ng-trim="false"
                                    ng-focus="showCrossIcon = true;"
                                    ng-keyup="intiatedBool && loginIntiatedGA()"
                                    ng-blur="showCrossIcon = false" ng-disabled="emailFieldDisable"
                                    tabindex="1"/>

                                <span class="number-prefix-new" ng-show="((sessionData.email | isMobile) && loginForm.username.$dirty &&
                                                    !loginForm.username.$error.required)">+91</span>

                                <div ng-messages="loginForm.username.$dirty">
                                                <span ng-show="loginForm.username.$dirty || showRequired">
                                                <span class="error" ng-show="loginForm.username.$error.required">Mobile/Email is required.</span>
                                                <span class="error"
                                                      ng-show="!(sessionData.email | isMobile) && loginForm.username.$error.emailValid">Email
                                                    incorrect.
                                                </span>
                                                <span class="error"
                                                      ng-show="(sessionData.email | isMobile) && loginForm.username.$error.mobileValid">Mobile
                                                    Number incorrect.
                                                </span>
                                                </span>

                                    <span class="error" ng-show="formError" ng-bind="formErrorMsg"></span>
                                    <!-- Error message from backend -->
                                    <span class="error"
                                          ng-show="sessionData.isInvalidUserNamePassword && !showRequired"
                                          ng-bind="sessionData.errorMessage"></span>
                                </div>

                            </md-input-container>

                            <!-- Mobile Only When Only OTP -->
                            <md-input-container ng-if="subTheme != 'panel' && (subTheme == 'scanandpay' || sessionData.minKycMandate == 'true')">
                                    <label ng-if="subTheme != 'scanandpay'">Enter Mobile</label>
                                    <label ng-if="subTheme == 'scanandpay'" ng-bind="text.mobileInputLabel"></label>

                                    <a class="clearMobileInput"
                                       ng-show="(subTheme == 'mp-html5' || subTheme == 'mall-html5') && sessionData.email && showCrossIcon"
                                       ng-click="sessionData.email = ''">
                                        <img src="/pages/themesv2/images/mp-html5/cross.svg">
                                    </a>

                                <input type="text" name="username"
                                       ng-class="{'number-new': ((sessionData.email | isMobile) && loginForm.username.$dirty && !loginForm.username.$error.required)}"
                                       ng-model="sessionData.email" autofill-input data-required mobile-validate numeric
                                       data-ng-trim="false"
                                       ng-focus="sessionData.formFailurerMsg = ''; showCrossIcon = true;hideBEMsg()"
                                       ng-blur="showCrossIcon = false ;" tabindex="1">
    
                                    <span class="number-prefix-new" ng-show="((sessionData.email | isMobile) && loginForm.username.$dirty &&
                                                        !loginForm.username.$error.required)">+91</span>
    
                                    <div ng-messages="loginForm.username.$dirty">
                                                    <span ng-show="loginForm.username.$dirty || showRequired">
                                                    <span class="error" ng-show="(loginForm.username.$error.required || loginForm.username.$error.parse)">Mobile is required.</span>
                                                    
                                                    <span class="error"
                                                          ng-show="(sessionData.email | isMobile) && loginForm.username.$error.mobileValid">Mobile
                                                        Number incorrect.
                                                    </span>
                                                    </span>
    
                                        <span class="error" ng-show="formError && subTheme != 'scanandpay'" ng-bind="sessionData.formFailurerMsg"></span>
                                        <span class="error" ng-show="formError && subTheme == 'scanandpay'" ng-bind="formErrorMsg"></span>
                                        <!-- Error message from backend -->
                                        <span class="error"
                                              ng-show="sessionData.isInvalidUserNamePassword && !showRequired"
                                              ng-bind="sessionData.errorMessage"></span>
                                    </div>
    
                            </md-input-container>
                            <!--password input-->
                            <md-input-container ng-if="showPass && subTheme != 'scanandpay' && !(sessionData.minKycMandate == 'true')">
                                <label ng-bind="text.passwordInputLabel"></label>
                                <a class="showPassword" ng-show="subTheme == 'mp-html5' || subTheme == 'mall-html5' || subTheme == 'mp-web' || subTheme == 'mp-mall' || subTheme == 'panel' || subTheme == 'dashboard'"
                                   ng-click="showPassClick()" tabindex="3">Hide</a>

                                <input type="text" name="password" maxlength="15" ng-disabled="otpVerify"
                                       ng-model="sessionData.password"
                                       data-required data-ng-trim="false" tabindex="2"
                                       ng-keyup="intiatedBool && loginIntiatedGA()"
                                       />

                                <div ng-messages="loginForm.password.$dirty">
                                                <span ng-show="(loginForm.password.$dirty && loginForm.password.$invalid) || showRequired">
                                                <span class="error"
                                                      ng-show="loginForm.password.$error.required && !otpVerify">Password is required.</span>
                                                </span>
                                </div>
                            </md-input-container>

                        <md-input-container ng-if="!showPass && subTheme != 'scanandpay' && !(sessionData.minKycMandate == 'true')">
                            <label ng-bind="text.passwordInputLabel"></label>
                            <a class="showPassword" ng-show="subTheme == 'mp-html5' || subTheme == 'mall-html5' || subTheme == 'mp-web' || subTheme == 'mp-mall' || subTheme == 'panel' || subTheme == 'dashboard'"
                                ng-click="showPassClick()" tabindex="3">Show</a>
                                <a class="showPassword" ng-click="forgetPasswordClick()" ng-show="subTheme == 'netbanking'" tabindex="3">Forgot Password?</a>

                                <input type="password" name="password" maxlength="15" ng-disabled="otpVerify"
                                       ng-model="sessionData.password"
                                       data-required data-ng-trim="false" placeholder="Paytm Password" tabindex="2"
                                       ng-keyup="intiatedBool && loginIntiatedGA()"
                                       >

                                <div ng-messages="loginForm.password.$dirty">
                                <span ng-show="(loginForm.password.$dirty && loginForm.password.$invalid) || showRequired">
                                    <span class="error" ng-show="loginForm.password.$error.required && !otpVerify">Password is required.</span>
                                </span>
                            </div>
                        </md-input-container>
                        <!-- Password Input -->
                        <span class="forgot-password-text-new" ng-if="subTheme == 'mp-web' || subTheme == 'mp-mall' || subTheme == 'panel' || subTheme == 'sellerpanel'">
                            <a ng-click="forgetPasswordClick()" tabindex="4" name="forgotClick" ga-clickevent
                            screen-name="/login"
                            event-category="login" event-action ="forgot_password_clicked"
                            event-type="customEvent"> Forgot Password</a><span class="separator">|</span><a tabindex="5" href="javascript:void(0)" ng-click="troubleLoggin()" ga-clickevent screen-name="/login"
                            event-category="login" event-action ="other_login_issues_clicked"
                            event-type="customEvent">Other Login Issues?</a>
                        </span>
                        <!-- <span class="forgot-password-text-new" ng-if="subTheme == 'scanandpay'">
                            <a ng-click="troubleLoggin()">Trouble logging in?</a>
                        </span> -->
                        <span class="forgot-password-text-new" ng-if="subTheme == 'diy' || subTheme == 'dashboard'|| subTheme == 'diy-ppb'">
                            <a ng-click="forgetPasswordClick()" tabindex="4">Forgot Password?</a>
                        </span>

                            <!-- Hidden Field -->
                            <input type="hidden" name="AUTH_STATE" ng-value="sessionData.authState"/>
                            <!-- Hidden Field -->
                            <div class="spinner-new" ng-if="subTheme != 'dashboard' && subTheme != 'diy' && subTheme != 'diy-ppb' && subTheme != 'netbanking'">
                                <md-progress-circular md-mode="indeterminate"
                                                      class="md-hue-2 md-primary load-white spinner-new-login"
                                                      ng-show="spinnerVisible" md-diameter="20"></md-progress-circular>
                            </div>


                    <md-button tabindex="6" class="md-raised md-primary btn-new mt-20 login-btn" type="submit"
                                ng-show="!otpVerify" ng-if="subTheme == 'mp-web'|| subTheme == 'mp-mall' || subTheme == 'panel'" ga-clickevent
                                   screen-name="/login"
                                   event-category="login" event-action ="login_proceed_clicked"
                                   event-type="customEvent"><img class="lock" ng-src="/pages/themesv2/images/mp-web/lock.svg"/>
                        Login Securely
                    </md-button>
                    <div class="row panel-lower-div" ng-if="subTheme == 'netbanking'" >
                            <ul>
                                <li class="terms-cond-new" >
                                    <span class="terms-text">By logging in, you agree to
                                    <a tabindex="6" href="https://appfaq.paytm.com/legal/#" target="_blank"
                                        ng-bind="text.TandCText"></a></span>
                                    <span class="terms-text">& <a tabindex="7"
                                                                    href="https://pages.paytm.com/privacy.html"
                                                                    target="_blank">Privacy Policy</a> of Paytm Payments Bank.</span>
                                </li>
                            </ul>
                            <md-button tabindex="8" class="md-raised md-primary btn-new mt-20 login-btn" type="submit"
                                    ng-show="!otpVerify" ga-clickevent>
                                Secure Sign in

                                <div class="spinner-new" ng-if="subTheme == 'netbanking'">
                                    <md-progress-circular md-mode="indeterminate"
                                                          class="md-hue-2 md-primary load-white spinner-new-login"
                                                          ng-show="spinnerVisible" md-diameter="20"></md-progress-circular>
                                </div>
                            </md-button>
                        </div>
                        <md-button class="md-raised md-primary btn-new mt-20 login-btn" type="button"
                            ng-click="loginByOtpClick()" ng-if="subTheme == 'scanandpay'" ga-clickevent>
                                Proceed
                        </md-button>
                         <md-button class="md-raised md-primary btn-new mt-20 login-btn" type="submit"
                                   ng-show="!otpVerify" ng-if="subTheme == 'sellerpanel'" ga-clickevent>
                            Authenticate
                        </md-button>

                        <ul ng-if="subTheme == 'dashboard'">
                            <li class="terms-cond-new" >
                                <span class="terms-text">By logging in you are accepting paytm
                                <a tabindex="7" href="https://appfaq.paytm.com/legal/#" target="_blank"
                                   ng-bind="text.TandCText"></a></span>
                                <span class="terms-text">& <a tabindex="8"
                                                              href="https://pages.paytm.com/privacy.html"
                                                              target="_blank">Privacy Policy.</a></span>
                            </li>
                        </ul>

                        <md-button class="md-raised md-primary btn-new mt-20 login-btn" type="submit"
                                   ng-show="!otpVerify" ng-if="subTheme == 'mp-html5' || subTheme == 'mall-html5' || subTheme == 'dashboard'" ga-clickevent><img class="lock" ng-if = "subTheme == 'mp-html5' || subTheme == 'mall-html5'" ng-src="/pages/themesv2/images/mp-html5/lock.svg"/>
                            Login Securely
                            <div class="spinner-new" ng-if="subTheme == 'dashboard'">
                                <md-progress-circular md-mode="indeterminate"
                                                      class="md-hue-2 md-primary load-white spinner-new-login"
                                                      ng-show="spinnerVisible" md-diameter="20"></md-progress-circular>
                            </div>
                        </md-button>

                        <md-button class="md-raised md-primary btn-new mt-20 borderRadiusSqure" type="submit"
                            ng-show="!otpVerify"  ng-disabled="diyLoginBtnDisabled" ng-class="{'cursor-default' : diyLoginBtnDisabled}" ng-if="subTheme == 'diy' || subTheme =='diy-ppb'"> Login
                            <div class="spinner-new">
                                <md-progress-circular md-mode="indeterminate"
                                                      class="md-hue-2 md-primary load-white spinner-new-login"
                                                      ng-show="spinnerVisible" md-diameter="20"></md-progress-circular>
                            </div>
                        </md-button>

                        <md-button class="md-raised md-primary btn-new mt-20" type="button" ng-show="otpVerify"
                                   ng-click="loginByOtpClick()" ng-class="{'btn-new-other' : subTheme == 'mp-html5' || subTheme == 'mall-html5'}"><img class="lock"
                                                                     ng-src="/pages/themesv2/images/mp-web/lock.svg"/>
                            Get OTP
                        </md-button>
                    </md-content>

                        <div class="forgot-password-text-new" ng-if="subTheme == 'mp-html5' || subTheme == 'mall-html5'">
                            <a ng-click="helpMeLogin()">Help me Login</a>
                        </div>

                        <div class="signup-text" ng-if="subTheme == 'diy'">
                            <span>New User? <a href="" ng-click="callSignUp()">Sign Up</a></span>
                        </div>

                        <div class="signup-text" ng-if="subTheme == 'dashboard'">
                            <a href="" ng-click="callSignUp()">Create a new Paytm account</a>
                        </div>


                    <ul>
                        <li class="terms-cond-new" ng-if="subTheme == 'mp-html5' || subTheme == 'mall-html5' || subTheme == 'mp-web' || subTheme == 'mp-mall'">
                            <span class="terms-text">By logging in, you agree to our
                            <a tabindex="7" href="https://appfaq.paytm.com/legal/#" target="_blank"
                               ng-bind="text.TandCText"></a></span>
                            <span class="terms-text">& <a tabindex="8"
                                                          href="https://pages.paytm.com/privacy.html"
                                                          target="_blank">Privacy Policy.</a></span>
                        </li>
                        <li class="terms-cond-new" ng-if="subTheme != 'mp-html5' && subTheme != 'mall-html5' && subTheme != 'mp-web' && subTheme != 'mp-mall' && subTheme != 'scanandpay' && subTheme != 'sellerpanel' && subTheme != 'diy' && subTheme != 'dashboard'&& subTheme != 'netbanking'">
                            <span class="terms-text">By logging in, you agree to our <a tabindex="7"
                                                                                        href="https://appfaq.paytm.com/legal/#"
                                                                                        target="_blank"
                                                                                        ng-bind="text.TandCText"></a></span>
                            <span class="terms-text">& <a tabindex="8"
                                                                                   href="https://pages.paytm.com/privacy.html"
                                                                                   target="_blank">Privacy Policy.</a></span>
                        </li>
                        <li class="terms-cond-new" ng-if="subTheme == 'sellerpanel'">
                             <span class="terms-text">You agree to <a tabindex="7" href="http://paytm.com/terms.html" target="_blank" ng-bind="text.TandCText"></a></span> <span class="terms-text">and <a tabindex="5" href="https://paytm.com/privacy-policy.html" target="_blank">Privacy Policy.</a></span>
                        </li>
                    </ul>

                    </div>

                <div ng-if="subTheme != 'mp-web' && subTheme != 'mp-mall' && subTheme != 'scanandpay' && subTheme != 'diy' && subTheme != 'mp-html5' && subTheme != 'mall-html5' &&subTheme != 'panel' && subTheme != 'netbanking'&& subTheme != 'diy-ppb' && subTheme != 'dashboard'">
                    <!-- Fake fields are a workaround for chrome autofill getting the wrong fields -->
                    <input style="display:none" type="text" name="fakeusernameremembered"/>
                    <input style="display:none" type="password" name="fakepasswordremembered"/>
                    <!-- Fake fields end-->
                    <h2 class="ump-header" ng-if="subTheme === 'ump'"ng-bind="text.loginLink">
                    </h2>
                    <div class="label-container">
                        <span ng-if="subTheme == 'panel'">
                            <label class="animate" ng-class="{'animate-show' : (isIE)}">Email</label>
                            <label class="animate"
                                   ng-class="{'animate-show' : (loginForm.username.$dirty && !loginForm.username.$error.required) && (sessionData.email | isMobile) && (!isIE)}">Email</label>
                            <label class="animate"
                                   ng-class="{'animate-show' : (loginForm.username.$dirty && !loginForm.username.$error.required) && (!(sessionData.email | isMobile)) && (!isIE)}">Email</label>
                        </span>

                            <span ng-if="subTheme != 'panel'">
                            <label class="animate" ng-class="{'animate-show' : (isIE)}">Mobile / Email</label>
                            <label class="animate"
                                   ng-class="{'animate-show' : (loginForm.username.$dirty && !loginForm.username.$error.required) && (sessionData.email | isMobile) && (!isIE)}">Mobile</label>
                            <label class="animate"
                                   ng-class="{'animate-show' : (loginForm.username.$dirty && !loginForm.username.$error.required) && (!(sessionData.email | isMobile)) && (!isIE)}">Email</label>
                        </span>
                        </div>

                        <div class="input-wrapper" ng-if="subTheme != 'panel'">
                            <input type="text" name="username" tabindex="1" placeholder="Enter your Mobile or Email"
                                   ng-class="{'number': ((sessionData.email | isMobile) && loginForm.username.$dirty &&
            !loginForm.username.$error.required)}"
                                   ng-model="sessionData.email" autofill-input
                                   data-required email-validate mobile-validate maxlength="199" data-ng-trim="false">

                            <span class="number-prefix" ng-show="((sessionData.email | isMobile) && loginForm.username.$dirty &&
            !loginForm.username.$error.required)">+91</span>

                            <div class="help-block">
                                <!-- Client Side Validation -->
                                <span ng-show="loginForm.username.$dirty || showRequired">
                                <span class="error" ng-show="loginForm.username.$error.required">Mobile/Email is required.</span>
                                <span class="error"
                                      ng-show="!(sessionData.email | isMobile) && loginForm.username.$error.emailValid">Email
                                incorrect.</span>
                                <span class="error"
                                      ng-show="(sessionData.email | isMobile) && loginForm.username.$error.mobileValid">Mobile
                                Number incorrect.</span>
                            </span>

                                <span class="error" ng-show="formError" ng-bind="formErrorMsg"></span>

                                <!-- Error message from backend -->
                                <span class="error"
                                      ng-show="sessionData.isInvalidUserNamePassword && !showRequired"
                                      ng-bind="sessionData.errorMessage"></span>

                            </div>
                        </div>

                        <div class="input-wrapper" ng-if="subTheme == 'panel'">

                            <input type="text" name="username" tabindex="1" placeholder="Enter your Email"
                                   ng-model="sessionData.email" autofill-input
                                   data-required email-validate maxlength="199" data-ng-trim="false">

                            <div class="help-block">
                                <!-- Client Side Validation -->
                                <span ng-show="loginForm.username.$dirty || showRequired">
                                <span class="error"
                                      ng-show="loginForm.username.$error.required">Email is required.</span>
                                <span class="error"
                                      ng-show="loginForm.username.$error.emailValid">Email Incorrect.</span>
                            </span>

                                <span class="error" ng-show="formError" ng-bind="formErrorMsg"></span>

                                <!-- Error message from backend -->
                                <span class="error"
                                      ng-show="sessionData.isInvalidUserNamePassword && !showRequired"
                                      ng-bind="sessionData.errorMessage">
                            </span>

                            </div>
                        </div>

                        <!-- Password Input -->
                        <div class="label-container">
                            <label class="animate"
                                   ng-class="{'animate-show' : (loginForm.password.$dirty && !loginForm.password.$error.required) || (isIE)}">Password</label>
                        </div>

                        <input type="password" name="password" tabindex="2" maxlength="15" placeholder="Paytm Password"
                               ng-disabled="otpVerify"
                               ng-model="sessionData.password" data-required data-ng-trim="false">
                        <div class="help-block">
                        <span ng-show="loginForm.password.$dirty && loginForm.password.$invalid || showRequired">
                            <span class="error" ng-show="loginForm.password.$error.required && !otpVerify">Password is required.</span>
                        </span>
                        </div>

                        <!-- Password Input -->
                        <div id="forgot-password-container">
                            <div><a ng-click="forgetPasswordClick()">Forgot Password?</a></div>
                            <span class="forgot-password-text">(Create a new password)</span>
                        </div>


                        <!-- Hidden Field -->
                        <input type="hidden" name="AUTH_STATE" ng-value="sessionData.authState"/>
                        <!-- Hidden Field -->


                        <div id="login-otp-container">
                            <input type="checkbox" tabindex="4" ng-model="$parent.otpVerify"
                                   ng-init="$parent.otpVerify = false" ng-if="otpOptionAvailable">
                            <span ng-if="otpOptionAvailable">Send me an OTP to Login.</span>
                        </div>

                    <div class="terms-cond">
                        <span class="terms-text">By logging in, you agree to our <a tabindex="5"
                                                                                    href="https://appfaq.paytm.com/legal/#"
                                                                                    target="_blank"
                                                                                    ng-bind="text.TandCText"></a></span>
                        <span class="terms-text">& <a tabindex="6"
                                                                               href="https://pages.paytm.com/privacy.html"
                                                                               target="_blank">Privacy Policy.</a></span>
                    </div>

                        <div class="button-wrapper">
                            <div class="spinner" ng-show="spinnerVisible"></div>
                            <button class="btn btn-primary" type="submit" ng-show="!otpVerify"
                                    ng-bind="text.loginText"></button>
                            <button class="btn btn-primary" type="button" ng-show="otpVerify"
                                    ng-click="loginByOtpClick()">
                                Get
                                OTP
                            </button>
                            <img class="arrow-image" src="/pages/themesv2/images/mp-web/arrow.png">
                        </div>
                    </div>

                </form>
            </div>
        </div>
        <!-- Trouble Loggin Container -->

        <div id="troubleLogginContainer" ng-show="troubleLoggginContainer">
            <div ng-if="subTheme != 'mp-html5' && subTheme != 'mall-html5'">
             <div class="header" ng-if="subTheme != 'scanandpay'">
                <a href="javascript:void(0)" ng-click="troubleLoggin()"><img src="/pages/themesv2/images/mp-web/back.svg"></a>
                <span>Trouble logging in?</span>
            </div>
                <h2 ng-if="subTheme == 'scanandpay'">Trouble logging in?</h2>
                <div class="innerContainer">
                    <p ng-if="subTheme == 'scanandpay'"><a ng-click="forgetPasswordClick()" style="cursor: pointer;" name="forgotClick" ga-clickevent>I
                        forgot my password</a></p>
                    <p>
                    <a screen-name="/login"
                    event-category="login" event-action ="other_login_issue_selected"
                    event-type="customEvent" event-label="I want to create a new password" ga-clickevent ng-click="forgetPasswordClick()" style="cursor: pointer;" name="forgotClick">I
                        want
                        to create a new password<span class="arrow"></span></a></p>
                    <p ga-clickevent screen-name="/login"
                    event-category="login" event-action ="other_login_issue_selected"
                    event-type="customEvent" event-label="I don't have my mobile number"><a href="https://paytm.com/care/myaccount/" target="_parent" style="cursor: pointer;">I don't
                        have my
                        mobile number<span class="arrow"></span></a></p>
                    <p ga-clickevent screen-name="/login"
                    event-category="login" event-action ="other_login_issue_selected"
                    event-type="customEvent" event-label="Contact us">
                    <a ng-href="{{subTheme == 'mp-mall' ? 'https://paytmmall.com/care/ticket' : 'https://paytm.com/care/ticket/'}}" target="_parent" style="cursor: pointer;">Contact us<span class="arrow"></span></a>
                    </p>
                    <br>
                    <md-button  ng-if="(subTheme != 'mp-web' && subTheme != 'mp-mall')" class="md-raised md-primary btn-new mt-20" style="width: auto; display: inherit;"
                               type="button" ng-click="troubleLoggin()">Back
                    </md-button>
                </div>
            </div>

            <div class="helpMeLogin" ng-if="subTheme == 'mp-html5' || subTheme == 'mall-html5'">
                <ul>
                    <li ng-click="forgetPasswordClick()" ga-clickevent screen-name="/login"
                    event-category="login" event-action ="other_login_issue_selected"
                    event-type="customEvent" event-label="I forgot my password" name="forgotClick"><img
                            src="/pages/themesv2/images/mp-html5/Forget_password.svg"><span>I forgot my password </span>
                    </li>
                    <li ng-click="redirect('myaccount')" ga-clickevent screen-name="/login"
                    event-category="login" event-action ="other_login_issue_selected"
                    event-type="customEvent" event-label="I do not have my mobile number"><img
                            src="/pages/themesv2/images/mp-html5/lost_mobile_no.svg"><span>I do not have my mobile number</span>
                    </li>
                    <li ng-click="redirect('ticket')" ga-clickevent screen-name="/login"
                    event-category="login" event-action ="other_login_issue_selected"
                    event-type="customEvent" event-label="I have some other issue"><img src="/pages/themesv2/images/mp-html5/other_issue.svg"><span>I have some other issue</span>
                    </li>
                </ul>
            </div>
            </div>
        </div>
        <!-- Wallet Container -->

<div id="wallet-container" ng-if="showWalletContainer && !isIvrFlow && subTheme != 'mp-web' && subTheme != 'mp-mall' && subTheme != 'scanandpay' && subTheme != 'netbanking' && subTheme != 'diy' && subTheme != 'panel' && subTheme != 'sellerpanel' && subTheme != 'ump'&& subTheme != 'diy-ppb' && subTheme != 'dashboard'">

            <div class="wallet-image-container">
                <img ng-src="/pages/themesv2/images/mp-web/wallet.png">
                <div class="wallet-heading">Advantages of Paytm wallet</div>
            </div>

            <div class="wallet-text-container">
                <div class="line-container">
                    <div class="sprite line-1"></div>
                    <span class="wallet-line-text">Pay your bills using Paytm Wallet</span></div>
                <div class="line-container">
                    <div class="sprite line-2"></div>
                    <span class="wallet-line-text">In case of refund, money will be credited to your wallet instantaneously</span>
                </div>
                <div class="line-container">
                    <div class="sprite line-3"></div>
                    <span class="wallet-line-text">Use Paytm Wallet on other websites</span></div>
            </div>

        </div>

    </div>
<!-- Wallet Container -->

<!-- Login Opt Container -->
<!--addMobile screen-->
</script>

<!--STYLESHEETS--><!--STYLESHEETS-->
<!--SCRIPTS--><script src="/pages/themesv2/scripts/paytmOauth.min.js?ver=1528794489924"></script><!--SCRIPTS-->
<script>
    var logoutToPaytm = "null";
    var logoutURL = "null";
    if (logoutToPaytm == "true") {
        window.top.location.href = logoutURL;
    } else {
        angular.element(document).ready(function() {
            angular.bootstrap(document, ['paytm-oauth']);
        });
    }
</script>
</body>
</html>

