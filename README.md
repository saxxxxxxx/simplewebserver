# EX01 Developing a Simple Webserver
## Date: 29.03.2024

## AIM:
To develop a simple webserver to serve html pages.

## DESIGN STEPS:
### Step 1: 
HTML content creation.

### Step 2:
Design of webserver workflow.

### Step 3:
Implementation using Python code.

### Step 4:
Serving the HTML pages.

### Step 5:
Testing the webserver.

## PROGRAM:
```
from http.server import HTTPServer, BaseHTTPRequestHandler 
content ="""
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <center><link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-QWTKZyjpPEjISv5WaRU9OFeRpok6YctnYmDr5pNlyT2bRjXh0JMhjY6hW+ALEwIH" crossorigin="anonymous">
    </center>
    <style>
        a{
          background-color: black;
            color: cadetblue;
            padding: 10px;
            text-decoration: none;
            font-size: 18px;
            font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
        }
        a:hover{
            color: crimson;
        }
        input{
            border-radius: 10px ;
            background-color: beige;
            color: black;
        }
        input:hover{
            color: blue;
            background-color: aliceblue;
        }
        *{
            font-family: 'Times New Roman', Times, serif;
        }
        div{
            
            font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
        }
        h1,h3{
            color: cadetblue;
        }
        
        
        .yu{
            background-color: rgb(0, 0, 0);
            text-decoration: underline;
        }
    </style>
</head>
<body style= "background-image: url(sam\ sulek.jpg);background-repeat: no-repeat;background-size: cover;background-attachment: fixed;">
  <div style="display: flex;">
    <div class="card" style="width: 18rem;margin: 15px;">
      <img src="fit.jpg" class="card-img-top" >
      <div class="card-body">
        <h5 class="card-title">Benefits of Physical Activity</h5>
        <p class="card-text">What are the benefits of fitness?
          Regular physical activity is one of the most important things you can do for your health. Being physically active can improve your brain health, help manage weight, reduce the risk of disease, strengthen bones and muscles, and improve your ability to do everyday activities.</p>
        <a href="https://www.cdc.gov/physicalactivity/basics/pa-health/index.htm" class="btn btn-primary">Read More</a>
      </div>
    </div>
    <div class="card" style="width: 18rem;margin: 15px;">
      <img src="fitshe.jpg" class="card-img-top" >
      <div class="card-body">
        <h5 class="card-title">Immediate Benefits</h5>
        <p class="card-text">Some benefits of physical activity on brain health [PDF-14.4MB] happen right after a session of moderate-to-vigorous physical activity. Benefits include improved thinking or cognition for children 6 to 13 years of age and reduced short-term feelings of anxiety for adults. Regular physical activity can help keep your thinking, learning, and judgment skills sharp as you age. It can also reduce your risk of depression and anxiety and help you sleep better.</p>
        <a href="https://www.cdc.gov/physicalactivity/basics/pa-health/index.htm" class="btn btn-primary">Read More</a>
      </div>
    </div>
    <div class="card" style="width: 18rem;margin: 15px;">
      <img src="fithe.jpg" class="card-img-top" >
      <div class="card-body">
        <h5 class="card-title">Weight Management</h5>
        <p class="card-text">Both eating patterns and physical activity routines play a critical role in weight management. You gain weight when you consume more calories through eating and drinking than the amount of calories you burn, including those burned during physical activity.</p>
        <a href="https://www.cdc.gov/physicalactivity/basics/pa-health/index.htm" class="btn btn-primary">Read More</a>
      </div>
    </div>
    <div class="card" style="width: 18rem;margin: 15px;">
      <img src="fithee.avif" class="card-img-top" >
      <div class="card-body">
        <h5 class="card-title">Strengthen Your Bones and Muscles</h5>
        <p class="card-text">As you age, it’s important to protect your bones, joints, and muscles – they support your body and help you move. Keeping bones, joints, and muscles healthy can help ensure that you’re able to do your daily activities and be physically active.

          Muscle-strengthening activities like lifting weights can help you increase or maintain your muscle mass and strength. This is important for older adults who experience reduced muscle mass and muscle strength with aging. Slowly increasing the amount of weight and number of repetitions you do as part of muscle strengthening activities will give you even more benefits, no matter your age.</p>
        <a href="https://www.cdc.gov/physicalactivity/basics/pa-health/index.htm" class="btn btn-primary">Read More</a>
      </div>
    </div>
  </div>
    <div style="display: flex;">
    <div style="width: 10%">
    <img src="fitlog.png" style="width: 100%;"></div>
    <div style="width: 70%">
    <a href="">Home</a>
    <a href="">About us</a>
    <a href="">Options</a>
    <a href="">Life at Gym</a>
    <a href="">Records</a></div>
    <div style="width: 10%">
    <img src="memlog.png" alt=""></div></div>

    <div style="width: 60%;height: 20%"><div id="carouselExampleIndicators" class="carousel slide">
        <div class="carousel-indicators">
          <button type="button" data-bs-target="#carouselExampleIndicators" data-bs-slide-to="0" class="active" aria-current="true" aria-label="Slide 1"></button>
          <button type="button" data-bs-target="#carouselExampleIndicators" data-bs-slide-to="1" aria-label="Slide 2"></button>
          <button type="button" data-bs-target="#carouselExampleIndicators" data-bs-slide-to="2" aria-label="Slide 3"></button>
        </div>
        <div class="carousel-inner">
          <div class="carousel-item active">
            <img src="ar.jpeg" class="d-block w-100" alt="...">
          </div>
          <div class="carousel-item">
            <img src="ro.jpeg" class="d-block w-100" alt="...">
          </div>
          <div class="carousel-item">
            <img src="ke.jpeg" class="d-block w-100" alt="...">
          </div>
        </div>
        <button class="carousel-control-prev" type="button" data-bs-target="#carouselExampleIndicators" data-bs-slide="prev">
          <span class="carousel-control-prev-icon" aria-hidden="true"></span>
          <span class="visually-hidden">Previous</span>
        </button>
        <button class="carousel-control-next" type="button" data-bs-target="#carouselExampleIndicators" data-bs-slide="next">
          <span class="carousel-control-next-icon" aria-hidden="true"></span>
          <span class="visually-hidden">Next</span>
        </button>
      </div></div>
    <div style="text-align: right;">
    <form>
        <input type="text"
        placeholder="Search"
        style="
        border-radius: 30px;
        height:50px;
        width:400px;
        background-image: url(search.png),url(fitness.png);
        background-size: contain;
        background-repeat: no-repeat;
        background-position: 2%,95%;
        text-align: center;">
        
    </form></div>
    <form method="get">
        <center><h1 class="yu">BUILD YOUR DREAM PHYSIQUE</h1><br>
        <h2 class="yu">MOVE MORE </h2><br>
    <h3>BE HEALTHY </h3></center>
        
        <center>
            <div style="color: blanchedalmond;height: fit-content;width: fit-content;"><form method="get">
              <input type="text" minlength="3" maxlength="10" required name = "fname" placeholder="First Name" title="enter minimum 3 characters"><br>
              <input type="text" minlength="3" maxlength="10" required name = "lname" placeholder="Last name" title="enter minimum 3 characters"><br>
              <input type="password" required name="pwd" placeholder="Password" title="Must contain one uppercase,one lower case,numericals,@ and any special characters."><br>
              
              
              <input type="email" required name="email id" placeholder="Enter your email"><br>
              
              <input type="number" min="6000000000" max="9999999999" required name="Phone Number" placeholder="Enter Phone Number"><br>
              DOB: <input type="date" required name="Date"><br>
              Gender: <input type="radio" name="gender" value="male">Male <br>
               <input type="radio" name="gender" value="female">Female <br>
               <h2>CHEST,TRI</h2>
               <h2>LAT,BI </h2>
               <h2>LEGS </h2>
               <h2>SHOULDERS,TRI </h2>
               <h2>LAT,BI</h2> 
               <h2>CHEST,SHOULDERS</h2> 
          
               CHOICE: <select name="choice">
          <h2></h2>      <option value="choice selection">---SELECT YOUR OPTION---</option>
                <option value="OPT 1">WEIGHT TRAINING</option>
                <option value="OPT 2">CARDIO+WEIGHT TRAINING</option>
                <option value="OPT 3">CARDIO</option>
                
              </select><br>
              <input type="submit" value="SAVE">
              <input type="reset" value="RESET ALL">
            </div>
            </form></center>
    </form>
    
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js" integrity="sha384-YvpcrYf0tY3lHB60NNkmXc5s9fDVZLESaAA55NDzOxhy9GkcIdslK1eN7N6jIeHz" crossorigin="anonymous"></script>
</body>
</html>
"""

class myhandler (BaseHTTPRequestHandler):
    def do_GET(self):
        print("request received")
        self.send_response(200)
        self.send_header('content-type', 'text/html; charset=utf-8')
        self.end_headers()
        self.wfile.write(content.encode())
server_address= ('',8000)
httpd=HTTPServer (server_address, myhandler)
print("my webserver is running...")
httpd.serve_forever()

```


## OUTPUT:
![ex1-1](https://github.com/saxxxxxxx/simplewebserver/assets/154911090/55bd89d8-7983-434c-b8d9-d375a1c74f36)

![ex1-2](https://github.com/saxxxxxxx/simplewebserver/assets/154911090/05db227d-804c-4f48-af3d-d48b4da995b4)

![ex1-3](https://github.com/saxxxxxxx/simplewebserver/assets/154911090/3f551aea-8c22-4bf4-baca-2474dc8b9338)

## RESULT:
The program for implementing simple webserver is executed successfully.
