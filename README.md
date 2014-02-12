Cloudinary on OpenShift in 5 Minutes
------------------------------------

This git repository helps you easily integrate Cloudinary's image management service into your Ruby OpenShift apps.

###Create your application###

1. Create an OpenShift account at http://openshift.redhat.com/ and set up you local machine with the client tools.
2. Sign up for a free Cloudinary account at https://cloudinary.com/users/register/free
3. Retrieve your account's CLOUDINARY_URL  from Cloudinary's dashboard.
4. Clone and deploy on OpenShift, supplying your CLOUDINARY_URL as application configuration details.  

```
    rhc app create cloudinary ruby-1.9 \
      --from-code https://github.com/cloudinary/cloudinary-openshift-ruby-quickstart.git \
      --env CLOUDINARY_URL=YOUR_CLOUDINARY_URL
```

The above example uses "cloudinary" as the application name. It also includes an application source URL, and several application configuration details.
If the `--from-code` option is not recognized, update your `rhc` gem.

If you failed to include your own CLOUDINARY_URL when creating your application, *don't worry* - There are notes on how to reconfigure your application in the next section.

When the command completes you should have your own clone of the application source code in a folder named after your app (`cloudinary`), and a live copy of your Photo Album sample application running at:

```
    http://cloudinary-$yournamespace.rhcloud.com
```

### Using Environment Variables
Use `rhc` to set the following environment variables for your OpenShift app (substituting in your own value):

    rhc env set CLOUDINARY_URL=YOUR_CLOUDINARY_URL -a cloudinary

Then, run the following to restart your application (reloading it's Cloudinary configuration):

    rhc app restart cloudinary

You can review your application's full list configuration keys by typing:

    rhc env list cloudinary

### Local Development
You can run the same code in a local development environment by populating the required environment variables in your local development stage:

    export CLOUDINARY_URL=YOUR_CLOUDINARY_URL

Then start your local server with:

    rails s

You may need to run `bundle install` before starting your local server to in order to make sure that your application has access to all of it's dependencies.
Next, you can edit your local source to start experimenting with Cloudinary.

When you're ready to deploy an update to OpenShift, `git add`, `git commit`, and `git push` can allow you to update your remote OpenShift example application using [a standard code development workflow](https://www.openshift.com/developers/deploying-and-building-applications).

More Information
----------------------------

Additional resources are available at:

* [Documentation for Ruby on Rails integration](http://cloudinary.com/documentation/rails_integration)
* [Ruby on Rails image upload documentation](http://cloudinary.com/documentation/rails_image_upload)
* [Ruby on Rails image manipulation documentation](http://cloudinary.com/documentation/rails_image_manipulation)
* [Image transformations documentation](http://cloudinary.com/documentation/image_transformations)
* [Knowledge Base](http://support.cloudinary.com/forums)
* [Documentation](http://cloudinary.com/documentation)
* [Cloudinary's Website](http://cloudinary.com)

