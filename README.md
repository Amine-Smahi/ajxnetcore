## What is Ajxnetcore
Its a creative way to turn an ASP.NET Core Application Into Single-Page Application,The goal is to minimize developer's effort while working on Creating an SPA, While improving the Software performance both on server and client side

## Why and How it works
Single page applications are more capable of decreasing load time of pages and the amount of data transfer from server to client. Why 1? There are several pain points while working with Javascript framework like AngularJs, React, VueJs, Knockout, meteor e.t.c. in a ASP.NET Core MVC application in order to create Single-Page Application.
#### Few Pain Points Are: 
* Need to specify routing for each request 
* Need to modify Server side technology according to Javascript framework 
* Only possible to debug on run time 
* Hard-coded data-binding caused too many error 
* Increase the complexity a lot
#### So what will i get
* No need to learn any javascript framework 
* No need to write much Jquery code to make Single Page Application 
* No need to write Jquery ajax code because the plugin has ajax function specified which will be called automatically as a common function
* Use default server side routing

#### Note: developer can also use other JavaScript framework(angularjs, knockout, react e.t.c.) side by side.

## How to setup
1) Download the js file from here and put it in the js directory ander the wwwroot folder
2) Replace the "_ViewStart.cshtml" file with 

        @{
          if (Context.Request.Headers["X-Requested-With"] == "XMLHttpRequest")
          {
              Context.Response.Headers["Location"] = Microsoft.AspNetCore.Http.Extensions.UriHelper.GetDisplayUrl(Context.Request);
              Context.Response.Headers["Cache-Control"] = "no-store";
          }
          else
          {
              Layout = "_Layout";
          }
        }

3) Add the reference of the ajxnetcore.js file in the "_layout.cshtml" file

        <script src="~/js/ajxnetcore.js"></script>
        
4) Put the RenderBody() inside a div with an id like this

        <div id="myid">@RenderBody()</div>  
        
5) Finnaly add the following lines just befor the closing body tag

        <script>
            $(function() {
                $('#myid').ajxnetcore();
            })
        </script>
