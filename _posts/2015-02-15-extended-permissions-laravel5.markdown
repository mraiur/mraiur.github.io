---
published: true
title: Extended permissions in Laravel 5
layout: post
tags: [php,laravel,laravel5,permissions]
categories: [php,laravel]
permalink: /2015/02/extended-permissions-in-laravel-5/
---
I need extended permission handling, but at the same time i don't like to copy-paste 2-3 lines with checks and redirects on each route handler.

So i use [https://github.com/Zizaco/entrust](https://github.com/Zizaco/entrust) for Roles and Permissions so in routes.php i have :

```
Route::get('test/{id}', ['uses' => 'TestController@index', 'middleware' => 'auth', 'access'=>['PERMISSION_KEY']]);
```

And 'access' is read in auth middleware like this :

```

public function handle($request, Closure $next)
{
    $options = $request->route()->getAction();

    if(isset($options['access'])){

        if(is_array($options['access']) && !canList($options['access'])){
            return redirect('auth/login');
        } else if(!can($options['access']) ) {
            return redirect('auth/login');
        }
    }

	if ($this->auth->guest())
	{
		if ($request->ajax())
		{
			return response('Unauthorized.', 401);
		}
		else
		{
			return redirect()->guest('auth/login');
		}
	}

	return $next($request);
}
```

So this way you can add access roles or pass a list of permissions etc..

That way you have one location to specify the permissions.
