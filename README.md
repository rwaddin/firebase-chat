# firebase-chat
Just for learning, how to use firebase authentication to secure realtime database with setting rule

# rule firebase
```json
{
  "rules": {
    "threads":{
       "$user_id" : {
         ".write" :"auth != null && auth.uid == $user_id && !data.exists()",
         ".read" : "auth != null && auth.uid == $user_id"
      }
    },
    "messages": {
      "$user_id" : {
        ".write" : "auth != null && auth.uid == $user_id",
        ".read" : "auth != null && auth.uid == $user_id"
      }
    }
  }
}
```
# firebase realtime structure
This is just for learning only. You can modify this script like all you want.
```json
{
    "threads": {
      "uid": {
        "firebaseid": {
          "referrer" : "",
          "started": "",
          "threadid": ""
        }
      }  
    },
    "messages": {
      "uid": {
        "firebaseid": {
          "aktor": "",
          "message": "",
          "status": "",
          "time" : ""
        }
      }
    }
}
```