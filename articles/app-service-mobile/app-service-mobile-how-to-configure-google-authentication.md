<properties
	pageTitle="How to configure Google authentication for your App Services application"
	description="Learn how to configure Google authentication for your App Services application."
    services="app-service\mobile"
	documentationCenter=""
	authors="mattchenderson" 
	manager="dwrede"
	editor=""/>

<tags
	ms.service="app-service-mobile"
	ms.workload="mobile"
	ms.tgt_pltfrm="na"
	ms.devlang="multiple"
	ms.topic="article"
	ms.date="11/20/2015"
	ms.author="mahender"/>

# How to configure your App Service application to use Google login

[AZURE.INCLUDE [app-service-mobile-selector-authentication](../../includes/app-service-mobile-selector-authentication.md)]
&nbsp;

[AZURE.INCLUDE [app-service-mobile-note-mobile-services](../../includes/app-service-mobile-note-mobile-services.md)]

This topic shows you how to configure Azure App Service to use Google as an authentication provider.

To complete the procedure in this topic, you must have a Google account that has a verified email address. To create a new Google account, go to [accounts.google.com](http://go.microsoft.com/fwlink/p/?LinkId=268302).

> [AZURE.NOTE]
This topic demonstrates use of the App Service Authentication / Authorization feature. This replaces the App Service gateway for most applications. Differences that apply to using the gateway are called out in notes throughout the topic.


## <a name="register"> </a>Register your application with Google

1. Log on to the [Azure portal], and navigate to your application. Copy your **URL**. You will use this to configure your Google app.
 
2. Navigate to the [Google apis](http://go.microsoft.com/fwlink/p/?LinkId=268303) website, sign-in with your Google account credentials, click **Create Project**, provide a **Project name**, then click **Create**.

3. In the left navigation bar, click **API & Auth**, then under **Social APIs** click **Google+ API** > **Enable API**.

4. Click **API & Auth** > **Credentials** > **OAuth consent screen**, then select your **Email address**,  enter a **Product Name**, and click **Save**.

5. In the **Credentials** tab, click **Add credentials** > **OAuth 2.0 client ID**, then select **Web application**.

6. Paste the App Service **URL** you copied earlier into **Authorized JavaScript Origins**, then paste the **Redirect URI** you copied earlier into **Authorized Redirect URI**. The redirect URI is the URL of your application appended with the path, _/.auth/login/google/callback_. For example, `https://contoso.azurewebsites.net/.auth/login/google/callback`. Make sure that you are using the HTTPS scheme. Then click **Create**.


	> [AZURE.NOTE]
	If you are using the App Service Gateway instead of the App Service Authentication / Authorization feature, your redirect URL instead uses the gateway URL with the _/signin-google_ path.


7. On the next screen, make a note of the values of the client ID and client secret.


    > [AZURE.IMPORTANT]
	The client secret is an important security credential. Do not share this secret with anyone or distribute it within a client application.


## <a name="secrets"> </a>Add Google information to your application

> [AZURE.NOTE]
If using the App Service Gateway, ignore this section and instead navigate to your gateway in the portal. Select **Settings**, **Identity**, and then **Google**. Paste in the values you obtained earlier and click **Save**.


8. Back in the [Azure portal], navigate to your application. Click **Settings**, and then **Authentication / Authorization**.

9. If the Authentication / Authorization feature is not enabled, turn the switch to **On**.

10. Click **Google**. Paste in the App ID and App Secret values which you obtained previously, and optionally enable any scopes your application requires. Then click **OK**.

    ![][1]

	By default, App Service provides authentication but does not restrict authorized access to your site content and APIs. You must authorize users in your app code. 

17. (Optional) To restrict access to your site to only users authenticated by Google, set **Action to take when request is not authenticated** to **Google**. This requires that all requests be authenticated, and all unauthenticated requests are redirected to Google for authentication.

12. Click **Save**. 

You are now ready to use Google for authentication in your app.

## <a name="related-content"> </a>Related Content

[AZURE.INCLUDE [app-service-mobile-related-content-get-started-users](../../includes/app-service-mobile-related-content-get-started-users.md)]


<!-- Anchors. -->

<!-- Images. -->

[0]: ./media/app-service-mobile-how-to-configure-google-authentication/mobile-app-google-redirect.png
[1]: ./media/app-service-mobile-how-to-configure-google-authentication/mobile-app-google-settings.png

<!-- URLs. -->

[Google apis]: http://go.microsoft.com/fwlink/p/?LinkId=268303

[Azure portal]: https://portal.azure.com/
 
