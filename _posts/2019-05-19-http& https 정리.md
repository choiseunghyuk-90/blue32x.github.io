#HTTP
```
HTTP(HyperText Transfer Protocol, 문화어: 초본문전송규약, 하이퍼본문전송규약)는 WWW 상에서 정보를 주고받을 수 있는 프로토콜이다.
주로 HTML 문서를 주고받는 데에 쓰인다. TCP와 UDP를 사용하며, 80번 포트를 사용한다. 1996년 버전 1.0, 그리고 1999년 1.1이 각각 발표되었다.
HTTP는 클라이언트와 서버 사이에 이루어지는 요청/응답(request/response) 프로토콜이다.
예를 들면, 클라이언트인 웹 브라우저가 HTTP를 통하여 서버로부터 웹페이지나 그림 정보를 요청하면, 서버는 이 요청에 응답하여 필요한 정보를 해당 사용자에게 전달하게 된다. 이 정보가 모니터와 같은 출력 장치를 통해 사용자에게 나타나는 것이다.
HTTP를 통해 전달되는 자료는 http:로 시작하는 URL(인터넷 주소)로 조회할 수 있다.
```
##JAVA HTTP  CONNECTION
```
          /*
			 * URL 객체에 connection을 열고자 하는  url을 셋팅한다.
			 * 1.https ,http 프로토콜에 따라 분기처리 가능하다.
			 */
			URL url = new URL("http://www.naver.com");
			/*
			 * url.openConnection()은 URLConnection 객체를 반환한다. 
			 * 이때 URLConnection객체를 상속하는 HttpURLConnection HttpsURLConnection객체로 명시적으로 
			 * 캐스팅해서 사용할 수 있다.
			 */
			HttpURLConnection urlCon = (HttpURLConnection)url.openConnection();
			
			/*
			 * 웹 브라우저가 서버에 접속하기 위해 소요된 시간이 connection을 구성하는데 소요된 시간이다.
			 * connectio을 구성하기 위해서 TCP connection과 동일한게 3-Handshake 방식을 수행한다.
			 * 
			 * 소요된 시간이  설정한 connectionTimeout시간을 넘으면  timeout 오류가 발생한다.
			 */
			urlCon.setConnectTimeout(1000);
			/*
			 *  client에서 sever에 요청데이터를 전송한 후 ,응답을 대기하는 시간이다.
			 *  단위는 ms이며 3000인 경우 3초를 대기한다.
			 */
			urlCon.setReadTimeout(3000);
			/*
			 * http Method
			 * GET,POST,HEAD,DELETE,PUT,OPTIONS,TRACE
			 */
			urlCon.setRequestMethod("GET");

```

##3-WAY HANDSHAKE
[설명](https://mindnet.tistory.com/entry/%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC-%EC%89%BD%EA%B2%8C-%EC%9D%B4%ED%95%B4%ED%95%98%EA%B8%B0-22%ED%8E%B8-TCP-3-WayHandshake-4-WayHandshake)

#HTTPS
```
HTTPS(HyperText Transfer Protocol over Secure Socket Layer, HTTP over TLS,HTTP over SSL,HTTP Secure)는 월드 와이드 웹 통신 프로토콜인 HTTP의 보안이 강화된 버전이다. HTTPS는 통신의 인증과 암호화를 위해 넷스케이프 커뮤니케이션즈 코퍼레이션이 개발했으며, 전자 상거래에서 널리 쓰인다.

HTTPS는 소켓 통신에서 일반 텍스트를 이용하는 대신에, SSL이나 TLS 프로토콜을 통해 세션 데이터를 암호화한다. 따라서 데이터의 적절한 보호를 보장한다. HTTPS의 기본 TCP/IP 포트는 443이다.

보호의 수준은 웹 브라우저에서의 구현 정확도와 서버 소프트웨어, 지원하는 암호화 알고리즘에 달려있다.

HTTPS를 사용하는 웹페이지의 URI은 'http://'대신 'https://'로 시작한다.
```

##JAVA HTTPS CONNECTION
```
		// TODO Auto-generated method stub
		try {
			
			/*
			 * URL 객체에 connection을 열고자 하는  url을 셋팅한다.
			 * 1.https ,http 프로토콜에 따라 분기처리 가능하다.
			 */
			URL url = new URL("http://www.naver.com");
			/*
			 * url.openConnection()은 URLConnection 객체를 반환한다. 
			 * 이때 URLConnection객체를 상속하는 HttpURLConnection HttpsURLConnection객체로 명시적으로 
			 * 캐스팅해서 사용할 수 있다.
			 */
			HttpsURLConnection urlCon = (HttpsURLConnection)url.openConnection();
			
			/*
			 * 웹 브라우저가 서버에 접속하기 위해 소요된 시간이 connection을 구성하는데 소요된 시간이다.
			 * connectio을 구성하기 위해서 TCP connection과 동일한게 3-Handshake 방식을 수행한다.
			 * 
			 * 소요된 시간이  설정한 connectionTimeout시간을 넘으면  timeout 오류가 발생한다.
			 */
			urlCon.setConnectTimeout(1000);
			/*
			 *  client에서 sever에 요청데이터를 전송한 후 ,응답을 대기하는 시간이다.
			 *  단위는 ms이며 3000인 경우 3초를 대기한다.
			 */
			urlCon.setReadTimeout(3000);
			/*
			 * http Method
			 * GET,POST,HEAD,DELETE,PUT,OPTIONS,TRACE
			 */
			urlCon.setRequestMethod("GET");
			
			
			
			urlCon.setHostnameVerifier(new HostnameVerifier() {  
				   @Override  
				   public boolean verify(String hostname, SSLSession session) {  
				    // Ignore host name verification. It always returns true.  
				    return true;  
				   }  
				     
			});  
			/*
			 *  SSL setting  
			 */
			  SSLContext context = SSLContext.getInstance("TLS");  
			  context.init(null, null, null);  // No validation for now  
			  urlCon.setSSLSocketFactory(context.getSocketFactory());  
			
			
			
		} catch (MalformedURLException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		} catch (IOException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		} catch (NoSuchAlgorithmException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		} catch (KeyManagementException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}

```

##TLS?SSL?
```
SSL(Secure Sockets Layer)은 보안 소켓 계층 이라는 뜻으로 인터넷을 통해 전달되는 정보 보안의 안전한 거래를 허용하기 위해 Netscape 사에서 개발한 인터넷 통신 규약 프로토콜이며, TLS(Transport Layer Security)는 SSL 3.0을 기초로 해서 IETF가 만든 프로토콜로 이는 SSL3.0을 보다 안전하게 하고 프로토콜의 스펙을 더 정확하고 안정성을 높이는 목적으로 고안되었습니다.
1.0 버전은 공개 된 적이 없고, 2.0 버전이 1995년 2월에 이르러 릴리스가 되지만 이 버전은 많은 보안 결함때문에 3.0 버전으로 곧바로 이어집니다.
3.0은 1996년 릴리스 되었고, 3.0 버전은 TLS 버전 1.0의 기초가 된 후, IETF에서 1999년 1월에 RFC 2246 표준 규약으로 정의하게 되었습니다.
SSL과 TLS 두 가지 프로토콜은 TCP/IP 네트워크를 사용하는 통신에 적용되며, 통신 과정 에서 전송계층 종단간 보안과 데이터 무결성을 확보 할 수 있게 합니다.

```
[참고](http://boansecurity.blogspot.com/2017/01/network-ssl-tls.html)
[참고WEBTOB](https://waspro.tistory.com/161)