## Guidance
Answer the following questions considering the learning outcomes for
- [Week 010](https://learn.foundersandcoders.com/course/syllabus/developer/week10-project05-DOTNET-intro/learning-outcomes/)

Make sure to record evidence of your processes. You can use code snippets, screenshots or any other material to support your answers.

Do not fill in the feedback section. The Founders and Coders team will update this with feedback on your progress.

## Assessment
 ### 1. Show evidence of some of the learning outcomes you have achieved this week.
 
-Week was good. In my team i had build the minimal api folder structure. Following the minimal API. 

-Also Following the minimal API workshop

-Battling to understand Object, instances, properties, methods. Somewhat come around the idea.

-Lightly delving into List<T> arrays. 

-Prompting chatgpt to explain to me what's going on. which are are accessors used  to  get and set  properties of said value in a class. 

```csharp
using System.Net.Http.Headers;
using Microsoft.OpenApi.Models;
using PizzaStore.DB;


var builder = WebApplication.CreateBuilder(args);

builder.Services.AddEndpointsApiExplorer();
builder.Services.AddCors(options => {});
if(builder.Environment.IsDevelopment())
{
    builder.Services.AddSwaggerGen(options =>
    {
        options.SwaggerDoc("v1", new OpenApiInfo 
        { 
            Title = "Todo API", 
            Description = "Keep track of your tasks",
             Version = "v1"});
    });
}
var app = builder.Build();
app.UseSwagger();
if (app.Environment.IsDevelopment())
{
   app.UseSwagger();
   app.UseSwaggerUI(c =>
   {
      c.SwaggerEndpoint("/swagger/v1/swagger.json", "PizzaStore API V1");
   });
}

app.MapGet("/pizzas/{id}", (int id) => PizzaDB.GetPizza(id));
app.MapGet("/pizzas", () => PizzaDB.GetPizzas());
app.MapPost("/pizzas", (Pizza pizza) => PizzaDB.CreatePizza(pizza));
app.MapPut("/pizzas", (Pizza pizza) => PizzaDB.UpdatePizza(pizza));
app.MapDelete("/pizzas/{id}", (int id) => PizzaDB.RemovePizza(id));

app.Run();
```


 ### 2. Show an example of some of the learning outcomes you have struggled with and/or would like to re-visit.
- So i need to go through microsoft certificate. As i had to prompt chatgpt alot on what's going on. with certain https requests such as post with the (Product product) 
- Look into controllers.
- Blazor.
- build something apart from the pizza minimal api.
- it was hard managing my time with the hackney presentation which i had to prepare for vigorously.  


## Feedback (For CF's)
> [**Course Facilitator name**]  
> [*What went well*]  
> [*Even better if*]
