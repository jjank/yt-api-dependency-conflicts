# yt-api-dependency-conflicts

Small reproducer to showcase that `com.google.apis:google-api-services-youtube:v3-rev20250224-2.0.0` has dependency conflicts.

## Build

`mvn validate` invokes the `maven-enforcer-plugin` applying the [`dependencyConvergence`](https://maven.apache.org/enforcer/enforcer-rules/dependencyConvergence.html) rule.

In particular there are **3 (!)** different versions of `com.google.http-client:google-http-client`:
* `com.google.http-client:google-http-client:jar:1.43.3`
* `com.google.http-client:google-http-client:jar:1.45.0`
* `com.google.http-client:google-http-client:jar:1.45.2`


```
[ERROR] Rule 0: org.apache.maven.enforcer.rules.dependency.DependencyConvergence failed with message:
[ERROR] Failed while enforcing releasability.
[ERROR] 
[ERROR] Dependency convergence error for com.google.http-client:google-http-client-gson:jar:1.43.3 paths to dependency are:
[ERROR] +-com.github.jjank.example:yt-dependency-conflicts:jar:1.0-SNAPSHOT
[ERROR]   +-com.google.apis:google-api-services-youtube:jar:v3-rev20250224-2.0.0:compile
[ERROR]     +-com.google.api-client:google-api-client:jar:2.7.2:compile
[ERROR]       +-com.google.oauth-client:google-oauth-client:jar:1.36.0:compile
[ERROR]         +-com.google.http-client:google-http-client-gson:jar:1.43.3:compile
[ERROR] and
[ERROR] +-com.github.jjank.example:yt-dependency-conflicts:jar:1.0-SNAPSHOT
[ERROR]   +-com.google.apis:google-api-services-youtube:jar:v3-rev20250224-2.0.0:compile
[ERROR]     +-com.google.api-client:google-api-client:jar:2.7.2:compile
[ERROR]       +-com.google.auth:google-auth-library-oauth2-http:jar:1.30.0:compile
[ERROR]         +-com.google.http-client:google-http-client-gson:jar:1.45.0:compile
[ERROR] and
[ERROR] +-com.github.jjank.example:yt-dependency-conflicts:jar:1.0-SNAPSHOT
[ERROR]   +-com.google.apis:google-api-services-youtube:jar:v3-rev20250224-2.0.0:compile
[ERROR]     +-com.google.api-client:google-api-client:jar:2.7.2:compile
[ERROR]       +-com.google.http-client:google-http-client-gson:jar:1.45.2:compile
[ERROR] 
[ERROR] 
[ERROR] Dependency convergence error for commons-codec:commons-codec:jar:1.17.1 paths to dependency are:
[ERROR] +-com.github.jjank.example:yt-dependency-conflicts:jar:1.0-SNAPSHOT
[ERROR]   +-com.google.apis:google-api-services-youtube:jar:v3-rev20250224-2.0.0:compile
[ERROR]     +-com.google.api-client:google-api-client:jar:2.7.2:compile
[ERROR]       +-commons-codec:commons-codec:jar:1.17.1:compile
[ERROR] and
[ERROR] +-com.github.jjank.example:yt-dependency-conflicts:jar:1.0-SNAPSHOT
[ERROR]   +-com.google.apis:google-api-services-youtube:jar:v3-rev20250224-2.0.0:compile
[ERROR]     +-com.google.api-client:google-api-client:jar:2.7.2:compile
[ERROR]       +-org.apache.httpcomponents:httpclient:jar:4.5.14:compile
[ERROR]         +-commons-codec:commons-codec:jar:1.11:compile
[ERROR] 
[ERROR] 
[ERROR] Dependency convergence error for com.google.guava:guava:jar:31.1-android paths to dependency are:
[ERROR] +-com.github.jjank.example:yt-dependency-conflicts:jar:1.0-SNAPSHOT
[ERROR]   +-com.google.apis:google-api-services-youtube:jar:v3-rev20250224-2.0.0:compile
[ERROR]     +-com.google.api-client:google-api-client:jar:2.7.2:compile
[ERROR]       +-com.google.oauth-client:google-oauth-client:jar:1.36.0:compile
[ERROR]         +-com.google.guava:guava:jar:31.1-android:compile
[ERROR] and
[ERROR] +-com.github.jjank.example:yt-dependency-conflicts:jar:1.0-SNAPSHOT
[ERROR]   +-com.google.apis:google-api-services-youtube:jar:v3-rev20250224-2.0.0:compile
[ERROR]     +-com.google.api-client:google-api-client:jar:2.7.2:compile
[ERROR]       +-com.google.auth:google-auth-library-oauth2-http:jar:1.30.0:compile
[ERROR]         +-com.google.guava:guava:jar:33.3.1-android:compile
[ERROR] and
[ERROR] +-com.github.jjank.example:yt-dependency-conflicts:jar:1.0-SNAPSHOT
[ERROR]   +-com.google.apis:google-api-services-youtube:jar:v3-rev20250224-2.0.0:compile
[ERROR]     +-com.google.api-client:google-api-client:jar:2.7.2:compile
[ERROR]       +-com.google.guava:guava:jar:33.1.0-jre:compile
[ERROR] 
[ERROR] 
[ERROR] Dependency convergence error for com.google.http-client:google-http-client:jar:1.43.3 paths to dependency are:
[ERROR] +-com.github.jjank.example:yt-dependency-conflicts:jar:1.0-SNAPSHOT
[ERROR]   +-com.google.apis:google-api-services-youtube:jar:v3-rev20250224-2.0.0:compile
[ERROR]     +-com.google.api-client:google-api-client:jar:2.7.2:compile
[ERROR]       +-com.google.oauth-client:google-oauth-client:jar:1.36.0:compile
[ERROR]         +-com.google.http-client:google-http-client:jar:1.43.3:compile
[ERROR] and
[ERROR] +-com.github.jjank.example:yt-dependency-conflicts:jar:1.0-SNAPSHOT
[ERROR]   +-com.google.apis:google-api-services-youtube:jar:v3-rev20250224-2.0.0:compile
[ERROR]     +-com.google.api-client:google-api-client:jar:2.7.2:compile
[ERROR]       +-com.google.auth:google-auth-library-oauth2-http:jar:1.30.0:compile
[ERROR]         +-com.google.http-client:google-http-client:jar:1.45.0:compile
[ERROR] and
[ERROR] +-com.github.jjank.example:yt-dependency-conflicts:jar:1.0-SNAPSHOT
[ERROR]   +-com.google.apis:google-api-services-youtube:jar:v3-rev20250224-2.0.0:compile
[ERROR]     +-com.google.api-client:google-api-client:jar:2.7.2:compile
[ERROR]       +-com.google.http-client:google-http-client:jar:1.45.2:compile

```