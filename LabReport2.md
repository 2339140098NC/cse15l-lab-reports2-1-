# Lab Report 2
## Code 
```
import java.io.IOException;
import java.net.URI;
import java.util.*;

class Handler implements URLHandler{
    private List<String> messages = new ArrayList<>();
	public String handleRequest(URI url){
	if (url.getPath().contains("/add-message")) {
            String query = url.getQuery();
            String[] parameters = query.split("&");
            String[] param1 = parameters[0].split("=");
            String[] param2 = parameters[1].split("=") ;//getQuery, contains meanning there are additional
            if (param1[0].equals("s") && param2[0].equals("user")) {
                //return String.format("%s: %s\n", param2[1],param1[1]);
                String message = param2[1] + ": " + param1[1];
                messages.add(message.replace("+", " "));
            }
        }
        StringBuilder response = new StringBuilder();
        for (String message : messages) {
            response.append(message).append("\n");
        }
        return response.toString();
	}
}

class ChatServer {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
}
```

![Image](1.png)
- ***Which methods in your code are called?*** The method handleRequest are called
- ***What are the relevant arguments to those methods, and the values of any relevant fields of the class?*** The relevant argument to the method handleRequest is URI url,: presents the request URI, which will be something like
  http://localhost:<port>/add-message?s=mudamudamuda&user=Nilloo. And List<String>=messages.
- ***How do the values of any relevant fields of the class change from this specific request?*** If no values got changed, explain why. The "messages" list in "handler changes from [] to ["Nilloo: mudamudamuda"]"
![Image](2.png)
- ***Which methods in your code are called?*** The method handleRequest are called
- ***What are the relevant arguments to those methods, and the values of any relevant fields of the class?*** The relevant argument to the method handleRequest is URI url,: presents the request URI, which will be something like
  http://localhost:<port>/add-message?s=Oraoraoraora!~&user=Jotaro. And List<String>=messages.
- ***How do the values of any relevant fields of the class change from this specific request?*** If no values got changed, explain why. The "messages" list in "handler changes from ["Nilloo: mudamudamuda"]" to ["Nilloo: mudamudamuda", "Jotaro: Oraoraoraora!~"]


## 

