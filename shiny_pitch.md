Coursera Developing Data Products Week 4 Assignment: Reproducible Pitch
============================================
author:  Ozge Tugrul Sonmez
autosize: true

date: 25.07.2020 



Coursera Peer Graded Assignment Reproducible Pitch
========================================================
autosize: true
You can find the details of the assignment from the web adress: 

https://www.coursera.org/learn/data-products/peer/tMYrn/course-project-shiny-application-and-reproducible-pitch

In this assignment, I prepared a shiny application and the link is : 

https://ozgetugrulsonmez.shinyapps.io/shiny_assignment/

Also, the codes of server.R and ui.R are on the link:

https://github.com/oztugrul/Developing-Data-Products-week-4




Data Used for Shiny Application
========================================================
width:1500
height:900

The data used for Shiny Application is mtcars data set.


```r
head(mtcars)
```

```
                   mpg cyl disp  hp drat    wt  qsec vs am gear carb
Mazda RX4         21.0   6  160 110 3.90 2.620 16.46  0  1    4    4
Mazda RX4 Wag     21.0   6  160 110 3.90 2.875 17.02  0  1    4    4
Datsun 710        22.8   4  108  93 3.85 2.320 18.61  1  1    4    1
Hornet 4 Drive    21.4   6  258 110 3.08 3.215 19.44  1  0    3    1
Hornet Sportabout 18.7   8  360 175 3.15 3.440 17.02  0  0    3    2
Valiant           18.1   6  225 105 2.76 3.460 20.22  1  0    3    1
```


ui.R
========================================================
autosize: true

```r
library(shiny)

shinyUI(
navbarPage("Developing Data Products Assignment",
           tabPanel("Simple Regression",
           (fluidPage(
  titlePanel("Predict Miles per Gallon (mpg) with Simple Regression Models"),
  sidebarLayout(
    sidebarPanel(
      selectInput("variable", "Select Input for Simple Regression",
                  c("am","cyl","hp","wt","disp","drat","qsec","gear","carb")),
      checkboxInput("simple_model","show simple model",value=FALSE),
      submitButton("Submit")
      
    ),
    mainPanel(
      h3("Simple Regression Model"),
      textOutput("model"),
      tabsetPanel(type = "tabs", 
                  tabPanel("BoxPlot", plotOutput("simpleboxplot"),textOutput("simpletext")),
                  tabPanel("Summary", verbatimTextOutput("simplesummary")),
                  tabPanel("Residual Plots", plotOutput("simpleresidual"))
                  
                  )))))),
  
  tabPanel("Multivariable Regression (Full)",
           fluidPage(
             titlePanel("Regression with All Variables for mpg Prediction"),
             sidebarLayout(
               sidebarPanel(
                 checkboxInput("multimodel","show full regression model",value=FALSE),
                 submitButton("Submit")
               ),
               mainPanel(
                 h3("Multivariable Regression Model"),
                 textOutput("fullmodel"),
                 tabsetPanel(type = "tabs", 
                             
                           tabPanel("Summary Full", verbatimTextOutput("multisummary")),
                           tabPanel("Residual Plots Full", plotOutput("multiresidual"))
                      
              ))))),
  tabPanel("Multivariable Regression (Variable Selection)",
           fluidPage(
             titlePanel("Regression with Best Variables for mpg Prediction"),
             sidebarLayout(
               sidebarPanel(
                 checkboxInput("show","Show/Hide Best Variable Subsets",value = FALSE),
                 checkboxInput("variablenum","Show/Hide Best Variable Number",value = FALSE),
                 checkboxInput("variables","Show/Hide Best Variables",value = FALSE),
                 
                 submitButton("Submit (it may take a while for processing)")
                 
               ),
               mainPanel(
                 h3("Best Subset Regression Model"),
                 verbatimTextOutput("bestvariablesubsets"),
                 verbatimTextOutput("variablenumber"),
                 verbatimTextOutput("bestvariables"),
                 
                 tabsetPanel(type = "tabs", 
                             
                             tabPanel("Summary ", verbatimTextOutput("multisummary2")),
                             tabPanel("Residual Plots", plotOutput("multiresidual2"))
                             
                 )))))))
```

<!--html_preserve--><nav class="navbar navbar-default navbar-static-top" role="navigation">
<div class="container-fluid">
<div class="navbar-header">
<span class="navbar-brand">Developing Data Products Assignment</span>
</div>
<ul class="nav navbar-nav" data-tabsetid="3009">
<li class="active">
<a href="#tab-3009-1" data-toggle="tab" data-value="Simple Regression">Simple Regression</a>
</li>
<li>
<a href="#tab-3009-2" data-toggle="tab" data-value="Multivariable Regression (Full)">Multivariable Regression (Full)</a>
</li>
<li>
<a href="#tab-3009-3" data-toggle="tab" data-value="Multivariable Regression (Variable Selection)">Multivariable Regression (Variable Selection)</a>
</li>
</ul>
</div>
</nav>
<div class="container-fluid">
<div class="tab-content" data-tabsetid="3009">
<div class="tab-pane active" data-value="Simple Regression" id="tab-3009-1">
<div class="container-fluid">
<h2>Predict Miles per Gallon (mpg) with Simple Regression Models</h2>
<div class="row">
<div class="col-sm-4">
<form class="well">
<div class="form-group shiny-input-container">
<label class="control-label" for="variable">Select Input for Simple Regression</label>
<div>
<select id="variable"><option value="am" selected>am</option>
<option value="cyl">cyl</option>
<option value="hp">hp</option>
<option value="wt">wt</option>
<option value="disp">disp</option>
<option value="drat">drat</option>
<option value="qsec">qsec</option>
<option value="gear">gear</option>
<option value="carb">carb</option></select>
<script type="application/json" data-for="variable" data-nonempty="">{}</script>
</div>
</div>
<div class="form-group shiny-input-container">
<div class="checkbox">
<label>
<input id="simple_model" type="checkbox"/>
<span>show simple model</span>
</label>
</div>
</div>
<div>
<button type="submit" class="btn btn-primary">Submit</button>
</div>
</form>
</div>
<div class="col-sm-8">
<h3>Simple Regression Model</h3>
<div id="model" class="shiny-text-output"></div>
<div class="tabbable">
<ul class="nav nav-tabs" data-tabsetid="7035">
<li class="active">
<a href="#tab-7035-1" data-toggle="tab" data-value="BoxPlot">BoxPlot</a>
</li>
<li>
<a href="#tab-7035-2" data-toggle="tab" data-value="Summary">Summary</a>
</li>
<li>
<a href="#tab-7035-3" data-toggle="tab" data-value="Residual Plots">Residual Plots</a>
</li>
</ul>
<div class="tab-content" data-tabsetid="7035">
<div class="tab-pane active" data-value="BoxPlot" id="tab-7035-1">
<div id="simpleboxplot" class="shiny-plot-output" style="width: 100% ; height: 400px"></div>
<div id="simpletext" class="shiny-text-output"></div>
</div>
<div class="tab-pane" data-value="Summary" id="tab-7035-2">
<pre id="simplesummary" class="shiny-text-output noplaceholder"></pre>
</div>
<div class="tab-pane" data-value="Residual Plots" id="tab-7035-3">
<div id="simpleresidual" class="shiny-plot-output" style="width: 100% ; height: 400px"></div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
<div class="tab-pane" data-value="Multivariable Regression (Full)" id="tab-3009-2">
<div class="container-fluid">
<h2>Regression with All Variables for mpg Prediction</h2>
<div class="row">
<div class="col-sm-4">
<form class="well">
<div class="form-group shiny-input-container">
<div class="checkbox">
<label>
<input id="multimodel" type="checkbox"/>
<span>show full regression model</span>
</label>
</div>
</div>
<div>
<button type="submit" class="btn btn-primary">Submit</button>
</div>
</form>
</div>
<div class="col-sm-8">
<h3>Multivariable Regression Model</h3>
<div id="fullmodel" class="shiny-text-output"></div>
<div class="tabbable">
<ul class="nav nav-tabs" data-tabsetid="9972">
<li class="active">
<a href="#tab-9972-1" data-toggle="tab" data-value="Summary Full">Summary Full</a>
</li>
<li>
<a href="#tab-9972-2" data-toggle="tab" data-value="Residual Plots Full">Residual Plots Full</a>
</li>
</ul>
<div class="tab-content" data-tabsetid="9972">
<div class="tab-pane active" data-value="Summary Full" id="tab-9972-1">
<pre id="multisummary" class="shiny-text-output noplaceholder"></pre>
</div>
<div class="tab-pane" data-value="Residual Plots Full" id="tab-9972-2">
<div id="multiresidual" class="shiny-plot-output" style="width: 100% ; height: 400px"></div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
<div class="tab-pane" data-value="Multivariable Regression (Variable Selection)" id="tab-3009-3">
<div class="container-fluid">
<h2>Regression with Best Variables for mpg Prediction</h2>
<div class="row">
<div class="col-sm-4">
<form class="well">
<div class="form-group shiny-input-container">
<div class="checkbox">
<label>
<input id="show" type="checkbox"/>
<span>Show/Hide Best Variable Subsets</span>
</label>
</div>
</div>
<div class="form-group shiny-input-container">
<div class="checkbox">
<label>
<input id="variablenum" type="checkbox"/>
<span>Show/Hide Best Variable Number</span>
</label>
</div>
</div>
<div class="form-group shiny-input-container">
<div class="checkbox">
<label>
<input id="variables" type="checkbox"/>
<span>Show/Hide Best Variables</span>
</label>
</div>
</div>
<div>
<button type="submit" class="btn btn-primary">Submit (it may take a while for processing)</button>
</div>
</form>
</div>
<div class="col-sm-8">
<h3>Best Subset Regression Model</h3>
<pre id="bestvariablesubsets" class="shiny-text-output noplaceholder"></pre>
<pre id="variablenumber" class="shiny-text-output noplaceholder"></pre>
<pre id="bestvariables" class="shiny-text-output noplaceholder"></pre>
<div class="tabbable">
<ul class="nav nav-tabs" data-tabsetid="3514">
<li class="active">
<a href="#tab-3514-1" data-toggle="tab" data-value="Summary ">Summary </a>
</li>
<li>
<a href="#tab-3514-2" data-toggle="tab" data-value="Residual Plots">Residual Plots</a>
</li>
</ul>
<div class="tab-content" data-tabsetid="3514">
<div class="tab-pane active" data-value="Summary " id="tab-3514-1">
<pre id="multisummary2" class="shiny-text-output noplaceholder"></pre>
</div>
<div class="tab-pane" data-value="Residual Plots" id="tab-3514-2">
<div id="multiresidual2" class="shiny-plot-output" style="width: 100% ; height: 400px"></div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div><!--/html_preserve-->

server.R
========================================================
autosize: true

```r
library(shiny)
library(ggplot2)
library(olsrr)
data(mtcars)

mtcars$cyl <- factor(mtcars$cyl)
mtcars$vs <- factor(mtcars$vs)
mtcars$gear <- factor(mtcars$gear)
mtcars$carb <- factor(mtcars$carb)
mtcars$am <- factor(mtcars$am,labels=c("Automatic","Manual"))

shinyServer(function(input, output) {
  
  full_model<-lm(mpg ~ am+cyl+hp+wt+disp+hp+drat+qsec+gear+carb,data=mtcars)
  best_model<-lm(mpg ~ am+hp+wt+disp+qsec,data=mtcars)
  
  formula<-reactive({
    paste("mpg ~", input$variable)
    
  })
  fit_simple<-reactive({
    lm(as.formula(formula()),data=mtcars)
  })
  
  output$model<-renderText({
    if(input$simple_model)
    {formula()}
  })
  
  output$simpleboxplot <- renderPlot({
    # check for the input variable
    if (input$variable == "am") {
      # am
      mpgData <- data.frame(mpg = mtcars$mpg, var = factor(mtcars[[input$variable]], labels = c("Automatic", "Manual")))
      p <- ggplot(mpgData, aes(var, mpg,fill=var)) + 
        geom_boxplot(alpha=0.3) + 
        xlab(input$variable)+scale_fill_brewer(palette="BuPu")
      print(p)
      
    }
    else if(input$variable == "cyl"|input$variable == "vs"|input$variable == "gear"|input$variable == "carb"){
      # cyl and gear
      mpgData <- data.frame(mpg = mtcars$mpg, var = factor(mtcars[[input$variable]]))
      p <- ggplot(mpgData, aes(var, mpg,fill=var)) + 
        geom_boxplot(alpha=0.3) + 
        xlab(input$variable)+scale_fill_brewer(palette="BuPu")
      print(p)
      
    }
    else{
      output$simpletext<-renderText({
        
        
        if (input$variable!= "am"|input$variable != "cyl"|input$variable!= "vs"|input$variable!= "gear"|input$variable!= "carb"){
          
          print("We don't have a categorical grouping variable!")
        }
      
      })
      
    }
    
  })
  
  output$simplesummary<-renderPrint({
    summary(fit_simple())
  })
    
  output$simpleresidual<-renderPlot({
    
    par(mfrow = c(2, 2))
    plot(fit_simple())
  })
  
  
  output$multisummary<-renderPrint({
    summary(full_model)
    
  })
  
  output$multiresidual<-renderPlot({
    
    par(mfrow = c(2, 2))
    plot(full_model)
  })
  
  output$bestvariablesubsets<-renderPrint({
    
    if(input$show)
    {ols_step_best_subset(full_model,details=TRUE)}
    else{"Check Show Hide Best Variable Subsets and Press Submit Button"}
   
  })
  
  output$fullmodel<-renderText({
    
    if(input$multimodel)
      {print("mpg ~ am+cyl+hp+wt+disp+hp+drat+qsec+gear+carb")}
  })
      
output$variablenumber<-renderPrint({
  
  if(input$variablenum)
  {adjr<-ols_step_best_subset(fit_multivariable_full,details = TRUE)$adjr
  which(adjr==max(adjr))}
  else{"Check Show Hide Best Variable Number and Press Submit Button"}
  
})

output$bestvariables<-renderPrint({
  
  if(input$variables)
  {
    adjr<-ols_step_best_subset(fit_multivariable_full,details = TRUE)$adjr
    var<-ols_step_best_subset(fit_multivariable_full,details = TRUE)$predictors[which(adjr==max(adjr))]
    print(var)
 }
  else{"Check Show Hide Best Variables and Press Submit Button"}
  
})

output$multisummary2<-renderPrint({
  summary(best_model)
  
  
})
output$multiresidual2<-renderPlot({
  
  par(mfrow = c(2, 2))
  plot(best_model)
})
})
```
