# Android Donkey Lock Kit SDK / Liveramp SDK conflict

Reproduction of conflict between Donkey Lock Kit and Liveramp SDK.
Gradle build fails with the following error:

```
Duplicate class a.a.a.f.a found in modules jetified-lockkit-1.1.0-SNAPSHOT-runtime (bike.donkey:lockkit:1.1.0-SNAPSHOT:20210923.095252-1)
  and jetified-plsdkandroid-v1.0.1-runtime (com.liveramp:plsdkandroid:v1.0.1)
```

Possible fix is to have the Donkey Lock Kit and Liveramp SDK change their builds to let ProGuard move obfuscated classes to a different root package.
See: https://github.com/Adyen/adyen-3ds2-android/issues/14

> We ended up using the flattenpackagehierarchy ProGuard option to move all our classes into a custom package. This does not guarantee the uniqueness of our package, but decreases the chance of a collision.

Documentation for the `-flattenpackagehierarchy` flag can be found on the [ProGuard website](https://www.guardsquare.com/manual/configuration/usage).
