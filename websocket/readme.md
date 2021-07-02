1.tomcat-websocket实现websocket(前端ws或wss协议，需要浏览器支持websocket)
1.1配置类
@Component
class{
	@Bean
	public ServerEndpointExporter serverEndpointExporter() {
		return new ServerEndpointExporter();
	}
}
1.2实现类
@Component
@ServerEndpoint(topicName)
class {
	@OnOpen
	open(Session session){}//前端websocket连接时调用
	@OnMessage
	message(String message){}//接收消息
	@OnClose
	close(Session session){}//前端websocket连接关闭时调用
	session.getAsyncRemote().sendText("message");//发送消息 发送异步消息
	session.getBasicRemote().sendText("message");//发送消息 发送同步消息
}
1.3前端实现
var webSocket3 = new WebSocket("ws://172.16.23.125:8088/queue/equipment/data");
webSocket3.onopen = function(){
	console.log("connect success");
	webSocket3.send("client send message to server");
};
webSocket3.onmessage = function(data){
	console.log("接收的消息:" + data.data)//接收消息
};
webSocket3.onclose = function(e){ 
  console.log("连接已关闭..."); 
  console.log("错误码：" + e.code);
  console.log("错误原因：" + e.reason);
};
2.spring提供的SimpMessagingTemplate实现websocket(stomp是websocket协议的一种(浏览器可以不支持websocket)，前端SockJS使用http或https，非ws和wss)
2.1配置类
@Configuration
@EnableWebSocketMessageBroker
class implements WebSocketMessageBrokerConfigurer {//SimpMessagingTemplate配置webSocket
	public void registerStompEndpoints(StompEndpointRegistry registry) {
		registry.addEndpoint("/webSocketServer").setAllowedOrigins("*").withSockJS();
	}
}
2.2实现类
@Component
class{//使用
	注入 SimpMessagingTemplate
	send(){
		simpMessagingTemplate.convertAndSend("topic",message)//发送消息
	}
}
2.3前端实现
var sockjs = new SockJS("http://172.16.23.125:8088/webSocketServer");
var stompClient = Stomp.over(sockjs);
stompClient.connect({},function connectCallback(frame){
	console.log("connect success");
	stompClient.subscribe(topicName, function(response){
		console.log("response.body:" + response.body)//接收消息
	});
})