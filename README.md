# uver
Code transformation for Unity/C#

Monkey Patching
----
The example below demonstrates how to __Monkey Patch__ existing method.
```cs
class CrazyMathPatch : Interceptor {
    public override bool IsTransformable(MethodData method)
        // parameters(0, 0) is not important because they never be called.
        => Match(method, () => Mathf.Max(0, 0)); 

    public float Max(float a, float b) {
        return Environment.TickCount % 2 == 1 ?
            a : b;
    }
}
```

Aspect Oriented Programming
----
```cs
class ProfileSampleAspect : Aspect {
  public override string attributeName => "TestAttribute";
  
  public override object Call(params object[] args) {
     Profiler.BeginSample("SAMPLE");
      var ret = CallOrigin(args);
     Profiler.EndSample();
     
     return ret;
  }
}
```
