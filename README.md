# uver
Code transformation for Unity/C#

Aspect Oriented Programming
```cs
class ProfileSampleAspect : AspectBase {
  public override string attributeName => "TestAttribute";
  
  public override object Call(params object[] args) {
     Profiler.BeginSample("SAMPLE");
      var ret = CallOrigin(args);
     Profiler.EndSample();
     
     return ret;
  }
}
```
