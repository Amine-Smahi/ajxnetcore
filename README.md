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
1) Download the js file from [here](https://raw.githubusercontent.com/Amine-Smahi/ajxnetcore/master/ajxnetcore.js) and put it in the js directory ander the wwwroot folder
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


## Screenshot
You can test this project by downloading the ajxnetcore.demo project

![ajxnetcore spa .net core asp](https://user-images.githubusercontent.com/24621701/50609498-1d5aff00-0ed0-11e9-9228-105cf21ef1d2.gif)



## License
The project is under [MIT License]() 

            Copyright (c) 2017 Amine Smahi

            Permission is hereby granted, free of charge, to any person obtaining a copy
            of this software and associated documentation files (the "Software"), to deal
            in the Software without restriction, including without limitation the rights
            to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
            copies of the Software, and to permit persons to whom the Software is
            furnished to do so, subject to the following conditions:

            The above copyright notice and this permission notice shall be included in all
            copies or substantial portions of the Software.

            THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
            IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
            FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
            AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
            LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
            OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
            SOFTWARE.
