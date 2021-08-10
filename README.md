# firebase-chat
Just for learning, how to use firebase authentication to secure realtime database with setting rule

# rule firebase
```json
{
  "rules": {
    "threads":{
      "$user_id" : {
        ".write" :"auth != null && auth.uid == $user_id && !data.exists()",
        ".read" : "auth != null && auth.uid == $user_id "
      },
      ".read" : "root.child('agents').hasChild(auth.uid)"
    },
    "messages": {
      "$user_id" : {
        ".write" : "auth != null && auth.uid == $user_id || root.child('agents').hasChild(auth.uid)",
        ".read" : "auth != null && auth.uid == $user_id"
      },
      ".read" : "root.child('agents').hasChild(auth.uid)"
    },
    "agents": {
      "$user_id": {
        ".write": "auth != null && auth.uid == $user_id && !data.exists()",
        ".read": "auth != null && auth.uid == $user_id"
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
    "<uid>": {
      "referrer" : "",
      "started": "",
      "threadid": ""
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
  },
	"agents": {
		"uid": {
			"dept": "",
			"mail": "",
			"ref": "",
			"uid": " "
		}
	}
}
```