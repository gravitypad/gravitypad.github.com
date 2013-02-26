---
layout: post
title: "Entity Framework: use properties for your entities"
date: 2011-03-31
comments: true
categories: 
---
I’ve been banging my head against what seemed to be a very simple problem. Using the new Entity Framework 4.1, I created a simple entity class:

``` c#
public class ElectricityMeasurement
{
    public int Id;
    public float Kwh;
    public float Volts;
    public long Ticks;
}
```

I kept getting an error complaining about no key being set for the entity:

``` c#
System.Data.Entity.ModelConfiguration.ModelValidationException :
One or more validation errors were detected during model generation:
 
System.Data.Edm.EdmEntityType: : EntityType 'ElectricityMeasurement'
has no key defined. Define the key for this EntityType.
 
System.Data.Edm.EdmEntitySet: EntityType: The EntitySet ElectricityMeasurements 
is based on type ElectricityMeasurement that has no keys defined.
```

But Entity Framework has conventions that should pick up the Id as the key? I even added a [Key] attribute to that property with no luck. Then it hit me: Entity Framework works with properties, not variables:

``` c#
public class ElectricityMeasurement
{
    public int Id { get; set; }
    public float Kwh { get; set; }
    public float Volts { get; set; }
    public long Ticks { get; set; }
}
```

And all is well.