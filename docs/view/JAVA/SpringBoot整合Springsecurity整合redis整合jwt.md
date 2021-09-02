---
title: "SpringBOot整合SpringSecurity+jwt+redis"
date: 2021-9-1 10:11:59
tags:
- '专业课'
categories:
- 'JAVA后端'
# 时间线
isTimeLine: true
---

## Spring Boot 整合 Spring security 整合 redis  整合  jwt

1. 创建Springboot 项目工程

   ![image-20210901161824194](/img/Spring Boot 整合 Spring security 整合 redis  整合  jwt\image-20210901161824194.png)

2. 选择好需要的jar 包依赖

   ![image-20210901161948904](/img/Spring Boot 整合 Spring security 整合 redis  整合  jwt\image-20210901161948904.png)

   ```xml
   <dependency>
       <groupId>com.baomidou</groupId>
       <artifactId>mybatis-plus-boot-starter</artifactId>
       <version>3.4.0</version>
   </dependency>
   
   <dependency>
       <groupId>com.baomidou</groupId>
       <artifactId>mybatis-plus-generator</artifactId>
       <version>3.4.1</version>
   </dependency>
   <dependency>
       <groupId>org.freemarker</groupId>
       <artifactId>freemarker</artifactId>
       <version>2.3.31</version>
   </dependency>
   
   <!-- jwt -->
   <dependency>
       <groupId>io.jsonwebtoken</groupId>
       <artifactId>jjwt-api</artifactId>
       <version>0.10.6</version>
   </dependency>
   <dependency>
       <groupId>io.jsonwebtoken</groupId>
       <artifactId>jjwt-impl</artifactId>
       <version>0.10.6</version>
   </dependency>
   <dependency>
       <groupId>io.jsonwebtoken</groupId>
       <artifactId>jjwt-jackson</artifactId>
       <version>0.10.6</version>
   </dependency>
   ```

3. 使用Mybatis-plus 代码生成器 生成以下几张表

   ```mysql
   
   -- ----------------------------
   -- Table structure for menu
   -- ----------------------------
   DROP TABLE IF EXISTS `menu`;
   CREATE TABLE `menu`  (
     `Id` int(11) NOT NULL AUTO_INCREMENT,
     `Name` varchar(150) CHARACTER SET utf8 COLLATE utf8_general_ci NOT NULL,
     `Href` varchar(50) CHARACTER SET utf8 COLLATE utf8_general_ci NULL DEFAULT NULL,
     `perm` varchar(50) CHARACTER SET utf8 COLLATE utf8_general_ci NOT NULL,
     `Type` int(11) NOT NULL,
     `Statu` int(11) NOT NULL,
     PRIMARY KEY (`Id`) USING BTREE,
     UNIQUE INDEX `perm`(`perm`) USING BTREE
   ) ENGINE = InnoDB AUTO_INCREMENT = 1 CHARACTER SET = utf8 COLLATE = utf8_general_ci ROW_FORMAT = Dynamic;
   
   -- ----------------------------
   -- Table structure for role
   -- ----------------------------
   DROP TABLE IF EXISTS `role`;
   CREATE TABLE `role`  (
     `Id` int(11) NOT NULL AUTO_INCREMENT,
     `RoleName` varchar(100) CHARACTER SET utf8 COLLATE utf8_general_ci NOT NULL,
     `Identify` varchar(100) CHARACTER SET utf8 COLLATE utf8_general_ci NOT NULL,
     `Remark` varchar(100) CHARACTER SET utf8 COLLATE utf8_general_ci NULL DEFAULT NULL,
     PRIMARY KEY (`Id`) USING BTREE,
     UNIQUE INDEX `RoleName`(`RoleName`) USING BTREE,
     UNIQUE INDEX `Identify`(`Identify`) USING BTREE
   ) ENGINE = InnoDB AUTO_INCREMENT = 1 CHARACTER SET = utf8 COLLATE = utf8_general_ci ROW_FORMAT = Dynamic;
   
   -- ----------------------------
   -- Table structure for role_menu
   -- ----------------------------
   DROP TABLE IF EXISTS `role_menu`;
   CREATE TABLE `role_menu`  (
     `RoleId` int(11) NOT NULL,
     `MenuId` int(11) NOT NULL,
     PRIMARY KEY (`RoleId`, `MenuId`) USING BTREE
   ) ENGINE = InnoDB CHARACTER SET = utf8 COLLATE = utf8_general_ci ROW_FORMAT = Dynamic;
   
   -- ----------------------------
   -- Table structure for users
   -- ----------------------------
   DROP TABLE IF EXISTS `users`;
   CREATE TABLE `users`  (
     `Id` int(11) NOT NULL AUTO_INCREMENT,
     `UserName` varchar(255) CHARACTER SET utf8 COLLATE utf8_general_ci NOT NULL,
     `Password` varchar(255) CHARACTER SET utf8 COLLATE utf8_general_ci NOT NULL,
     `Avatar` varchar(255) CHARACTER SET utf8 COLLATE utf8_general_ci NULL DEFAULT NULL,
     PRIMARY KEY (`Id`) USING BTREE,
     UNIQUE INDEX `UserName`(`UserName`) USING BTREE
   ) ENGINE = InnoDB AUTO_INCREMENT = 2 CHARACTER SET = utf8 COLLATE = utf8_general_ci ROW_FORMAT = Dynamic;
   
   -- ----------------------------
   -- Table structure for users_role
   -- ----------------------------
   DROP TABLE IF EXISTS `users_role`;
   CREATE TABLE `users_role`  (
     `UsersId` int(11) NOT NULL,
     `RoleId` int(11) NOT NULL,
     PRIMARY KEY (`RoleId`, `UsersId`) USING BTREE
   ) ENGINE = InnoDB CHARACTER SET = utf8 COLLATE = utf8_general_ci ROW_FORMAT = Dynamic;
   ```

   代码生成器 在官网 复制的就行

   ```java
   // 演示例子，执行 main 方法控制台输入模块表名回车自动生成对应项目目录中
   public class CodeGenerator {
   
       /**
        * <p>
        * 读取控制台内容
        * </p>
        */
       public static String scanner(String tip) {
           Scanner scanner = new Scanner(System.in);
           StringBuilder help = new StringBuilder();
           help.append("请输入" + tip + "：");
           System.out.println(help.toString());
           if (scanner.hasNext()) {
               String ipt = scanner.next();
               if (StringUtils.isNotBlank(ipt)) {
                   return ipt;
               }
           }
           throw new MybatisPlusException("请输入正确的" + tip + "！");
       }
   
       public static void main(String[] args) {
           // 代码生成器
           AutoGenerator mpg = new AutoGenerator();
   
           // 全局配置
           GlobalConfig gc = new GlobalConfig();
           String projectPath = System.getProperty("user.dir");
           gc.setOutputDir(projectPath + "/src/main/java");
           gc.setAuthor("大水");
           gc.setOpen(false);
           // gc.setSwagger2(true); 实体属性 Swagger2 注解
   //        gc.setServiceName("%Service");
           mpg.setGlobalConfig(gc);
   
           // 数据源配置
           DataSourceConfig dsc
                   = new DataSourceConfig();
           dsc.setUrl("jdbc:mysql://localhost:3306/admin?useUnicode=true&useSSL=false&characterEncoding=utf8");
           // dsc.setSchemaName("public");
           dsc.setDriverName("com.mysql.cj.jdbc.Driver");
           dsc.setUsername("root");
           dsc.setPassword("123456");
           mpg.setDataSource(dsc);
   
           // 包配置
           PackageConfig pc = new PackageConfig();
   //        pc.setModuleName(scanner("模块名"));
           pc.setModuleName("");
           pc.setParent("com.admin");
           mpg.setPackageInfo(pc);
   
           // 自定义配置
           InjectionConfig cfg = new InjectionConfig() {
               @Override
               public void initMap() {
                   // to do nothing
               }
           };
   
           // 如果模板引擎是 freemarker
           String templatePath = "/templates/mapper.xml.ftl";
           // 如果模板引擎是 velocity
           // String templatePath = "/templates/mapper.xml.vm";
   
           // 自定义输出配置
           List<FileOutConfig> focList = new ArrayList<>();
           // 自定义配置会被优先输出
           focList.add(new FileOutConfig(templatePath) {
               @Override
               public String outputFile(TableInfo tableInfo) {
                   // 自定义输出文件名 ， 如果你 Entity 设置了前后缀、此处注意 xml 的名称会跟着发生变化！！
                   return projectPath + "/src/main/resources/mapper/" + pc.getModuleName()
                           + "/" + tableInfo.getEntityName() + "Mapper" + StringPool.DOT_XML;
               }
           });
           /*
           cfg.setFileCreate(new IFileCreate() {
               @Override
               public boolean isCreate(ConfigBuilder configBuilder, FileType fileType, String filePath) {
                   // 判断自定义文件夹是否需要创建
                   checkDir("调用默认方法创建的目录，自定义目录用");
                   if (fileType == FileType.MAPPER) {
                       // 已经生成 mapper 文件判断存在，不想重新生成返回 false
                       return !new File(filePath).exists();
                   }
                   // 允许生成模板文件
                   return true;
               }
           });
           */
           cfg.setFileOutConfigList(focList);
           mpg.setCfg(cfg);
   
           // 配置模板
           TemplateConfig templateConfig = new TemplateConfig();
   
           // 配置自定义输出模板
           //指定自定义模板路径，注意不要带上.ftl/.vm, 会根据使用的模板引擎自动识别
           // templateConfig.setEntity("templates/entity2.java");
           // templateConfig.setService();
           // templateConfig.setController();
   
           templateConfig.setXml(null);
           mpg.setTemplate(templateConfig);
   
           // 策略配置
           StrategyConfig strategy = new StrategyConfig();
           strategy.setNaming(NamingStrategy.underline_to_camel);
           strategy.setColumnNaming(NamingStrategy.underline_to_camel);
   //        strategy.setSuperEntityClass("BaseEntity");
   //        strategy.setSuperEntityClass("你自己的父类实体,没有就不用设置!");
           strategy.setEntityLombokModel(true);
           strategy.setRestControllerStyle(true);
           // 公共父类
   //        strategy.setSuperControllerClass("你自己的父类控制器,没有就不用设置!");
   //        strategy.setSuperControllerClass("BaseController");
           // 写于父类中的公共字段
   //        strategy.setSuperEntityColumns("id","created","updated","statu");
           strategy.setInclude(scanner("表名，多个英文逗号分割").split(","));
           strategy.setControllerMappingHyphenStyle(true);
           strategy.setTablePrefix(pc.getModuleName() + "_");
           mpg.setStrategy(strategy);
           mpg.setTemplateEngine(new FreemarkerTemplateEngine());
           mpg.execute();
       }
   
   }
   ```

   这里数据裤就一条数据(之说 spring security 不写那么多 数据库)

   ![image-20210901163104538](/img/Spring Boot 整合 Spring security 整合 redis  整合  jwt\image-20210901163104538.png)

4. 配置配置类

   1. Redis 配置类

      ```java
      @Configuration
      public class RedisConfig extends CachingConfigurerSupport {
      
          @Bean
          public RedisTemplate<String, Object> redisTemplate(RedisConnectionFactory factory) {
              RedisTemplate<String, Object> template = new RedisTemplate<>();
              RedisSerializer<String> redisSerializer = new StringRedisSerializer();
              Jackson2JsonRedisSerializer jackson2JsonRedisSerializer = new Jackson2JsonRedisSerializer(Object.class);
              ObjectMapper om = new ObjectMapper();
              om.setVisibility(PropertyAccessor.ALL, JsonAutoDetect.Visibility.ANY);
              om.enableDefaultTyping(ObjectMapper.DefaultTyping.NON_FINAL);
              jackson2JsonRedisSerializer.setObjectMapper(om);
              template.setConnectionFactory(factory);
              //key序列化方式
              template.setKeySerializer(redisSerializer);
              //value序列化
              template.setValueSerializer(jackson2JsonRedisSerializer);
              //value hashMap序列化
              template.setHashValueSerializer(jackson2JsonRedisSerializer);
              template.setHashKeySerializer(jackson2JsonRedisSerializer);
              return template;
          }
      
          }
      }
      
      ```

   2. mybatis-plus 配置类

      ```java
      @Configuration
      @MapperScan("com.admin.mapper")
      public class MybatisConfig {
      }
      ```

5. 加入工具类跟数据封装类

   1. JwtUtils

      ```java
      @Data
      @Component
      @ConfigurationProperties(prefix = "jwt")
      public class JwtTokenUtils {
      
      //
         private String Header ;
      // 盐
         private String Secret ;
      // 颁发者标识
         private String Iss;
      
         // 过期时间是3600秒，既是1个小时
         private long Expiration ;
      
         // 创建token
         public  String createToken(String username) {
            return Jwts.builder()
                  .signWith(SignatureAlgorithm.HS512, Secret)
                  .setIssuer(Iss)
                  .setSubject(username)
                  .setIssuedAt(new Date())
                  .setExpiration(new Date(System.currentTimeMillis() + Expiration * 1000))
                  .compact();
         }
      
         // 从token中获取用户名
         public  String getUsername(String token){
            return getTokenBody(token).getSubject();
         }
      
         // 是否已过期
         public  boolean isExpiration(String token){
            return getTokenBody(token).getExpiration().before(new Date());
         }
      
      // 获取body 信息
         private  Claims getTokenBody(String token){
            return Jwts.parser()
                  .setSigningKey(Secret)
                  .parseClaimsJws(token)
                  .getBody();
         }
      }
      ```

   2. Redis 配置 ，网上随便搜一下就行了

   3. Result 数据封装类 (例子) 网上岁表找一个就行了

      ```java
      @NoArgsConstructor
      @AllArgsConstructor
      @Data
      public class Result implements Serializable {
          private int code;
          private String msg;
          private Map<String,Object> data = new HashMap<>();
      
          public static Result success(Map<String,Object> data){
              Result result = new Result();
              result.code = 200;
              result.msg = "成功";
              result.data = data;
              return result;
          }
          public static Result fail(String msg){
              Result result = new Result();
              result.code = 400;
              result.msg = msg;
              return result;
          }
      }
      ```

   4. 输出数据封装类

      ```java
      public class ResponseUtil {
      
          public static void out(HttpServletResponse response, Result r) {
              ObjectMapper mapper = new ObjectMapper();
              response.setStatus(HttpStatus.OK.value());
              response.setContentType(MediaType.APPLICATION_JSON_UTF8_VALUE);
              try {
                  mapper.writeValue(response.getWriter(), r);
              } catch (IOException e) {
                  e.printStackTrace();
              }
          }
      }
      ```

6. **重点来了 配置 Springsecurity 配置类**

   先配置好基本的

   ```java
   @Configuration
   @EnableWebSecurity
   @EnableGlobalMethodSecurity(prePostEnabled = true)
   public class SecurityConfig extends WebSecurityConfigurerAdapter {
         private static final String[] URL_WHITELIST = {"/login", "/logout", "/captcha","/test", "/favicon.ico"};
       // 密码加密类 引入后自动生效
       @Bean
       public BCryptPasswordEncoder passwordEncoder() {
           return new BCryptPasswordEncoder();
       }
       
   	// 核心配置类   
         @Override
       protected void configure(HttpSecurity http) throws Exception {
           http
               // 打开跨域共享
               .cors().and()
               // 关闭跨域请求保护
               .csrf().disable()
               // 关闭 session
                   .sessionManagement()
                   .sessionCreationPolicy(SessionCreationPolicy.STATELESS)
                   .and()
           	// 设置 请求控制   
                   .authorizeRequests()
            	// 设置指定请求 可以匿名   
                   .antMatchers(URL_WHITELIST).permitAll()
               // 其他请求 只有登陆后才可以访问
                   .anyRequest().authenticated()
       }
   }
   ```

7. 配置 application.yaml 配置文件

   ```yaml
   server:
     port: 8081
   
   spring:
     security:
       user:
         name: user
         password: $2a$10$IhKaUSLaiqMCVmdqRv2KgO5H5hGCIZ6JwVvY3vfW9z8/Xy49vf.Y2
     datasource:
     ... 不细说 自己找
     ... 顺便把 mybatis-plus 配置了
   redis:
       port: 6399
       host: 127.0.0.1
       connect-timeout: 1800000
   
   
   logging.level.com.admin: debug
   
   jwt:
     secret: sadjkljaklsjdkl5456zxclsadlsakdkalsjdklasjsadjkljaklsjdkl5456zxclsadlsakdkalsjdklasjsadjkljaklsjdkl5456zxclsadlsakdkalsjdklasj
     header: Authorization
     iss: lidashui.top
     expiration: 36000
   ```

8. 开始重写 第一个Spring security 过滤类 ，（看不懂去看看 security 的过滤链 ，执行顺序）

   1. **第一个类 UsernamePasswordAuthenticationFilter 他用来处理 /login请求的 其他请求不处理**

      ```java
      @Slf4j
      public class TokenUsernamePasswordFilter extends UsernamePasswordAuthenticationFilter {
      
          private AuthenticationManager authenticationManager;
          private JwtTokenUtils jwtTokenUtils;
          private RedisUtil redisUtil;
          public TokenUsernamePasswordFilter(AuthenticationManager authenticationManager, JwtTokenUtils jwtTokenUtils, RedisUtil redisUtil) {
              this.authenticationManager = authenticationManager;
              this.jwtTokenUtils = jwtTokenUtils;
              this.redisUtil = redisUtil;
          }
      
          @Override
          public Authentication attemptAuthentication(HttpServletRequest request, HttpServletResponse response) throws AuthenticationException {
              try {
      //            获取表单提交的用户名密码
                  SecurityUser securityUser = new ObjectMapper().readValue(request.getInputStream(), SecurityUser.class);
                  log.info("傻逼开门我来登录了");
      //            把账号密码 拿去认证 拿去 UserDetailService
                  return authenticationManager.authenticate( new UsernamePasswordAuthenticationToken(securityUser.getUsername(),securityUser.getPassword(),new ArrayList<>()));
              } catch (IOException e) {
                  e.printStackTrace();
                  throw  new RuntimeException(e.getMessage());
              }
          }
      
          @Override
          protected void successfulAuthentication(HttpServletRequest request, HttpServletResponse response, FilterChain chain, Authentication authResult) throws IOException, ServletException {
      //        认证成功，得到认证成功过后的用户信息
              SecurityUser principal = (SecurityUser) authResult.getPrincipal();
      //        根据用户名生成 token
              String token = jwtTokenUtils.createToken(principal.getUsername());
      //        把用户名 和 用户权限 放到 redis
      //          把获取到的 权限放到redis
              redisUtil.set(principal.getUsername(),principal.getPermission());
      //         设置响应头
              response.setHeader(jwtTokenUtils.getHeader(),token);
      //        返回 touken
              ResponseUtil.out(response,Result.success().data("token",token));
          }
      
          @Override
          protected void unsuccessfulAuthentication(HttpServletRequest request, HttpServletResponse response, AuthenticationException failed) throws IOException, ServletException {
              ResponseUtil.out(response, Result.fail("账号或者密码错误"));
          }
      }
      
      ```

   2. **第二个类 UserDetailsService 处理 查询数据库然后 认证 以及 权限的添加**

      ```java
      @Service("userDetailsService")
      public class UserDetailServiceImpl implements UserDetailsService {
          @Autowired
          IUsersService usersService;
      
      
          @Override
          public UserDetails loadUserByUsername(String s) throws UsernameNotFoundException {
      //        拿到 传过来的 username 去数据库查询 
              Users username = usersService.getOne(new QueryWrapper<Users>().eq("username", s));
      //        差不多 抛出 异常 用户不存在
              if(username == null){
                  throw new UsernameNotFoundException("用户不存在");
              }
      //        存在获取权限
              List<String> permission= new ArrayList<>();
      //        懒得写数据库了， 直接模拟 权限
              permission.add("admin");
              return new SecurityUser(username.getUsername(),username.getPassword(), permission);
          }
      }
      ```

      在 spring scurity 添加 过滤器

      ```java
      //                添加重写的过滤器
                      http.addFilter(new TokenUsernamePasswordFilter(authenticationManager(), jwtTokenUtils, redisUtil))
      ```

      还有 使用重写的UserDetailsService

      ```java
      @Override
      protected void configure(AuthenticationManagerBuilder auth) throws Exception {
          auth.userDetailsService(userDetailsService);
      }
      ```

   3. 重写 BasicAuthenticationFilter

      ```java
      @Slf4j
      public class TokenAuthFilter extends BasicAuthenticationFilter {
      
      
          private JwtTokenUtils jwtTokenUtils;
          private RedisUtil redisUtil;
          public TokenAuthFilter(AuthenticationManager authenticationManager,JwtTokenUtils jwtTokenUtils,RedisUtil redisUtil) {
              super(authenticationManager);
              this.jwtTokenUtils =jwtTokenUtils;
              this.redisUtil = redisUtil;
          }
      
          @Override
          protected void doFilterInternal(HttpServletRequest request, HttpServletResponse response, FilterChain chain) throws IOException, ServletException {
      //        获取当前的登录的token
              UsernamePasswordAuthenticationToken authentication = getAuthentication(request);
      //        如果有token 把token 放到当前 上下文中
              if(authentication != null){
                  SecurityContextHolder.getContext().setAuthentication(authentication);
              }
      
              chain.doFilter(request,response);
          }
      
          private UsernamePasswordAuthenticationToken getAuthentication(HttpServletRequest request){
      //        获取token
              String header = request.getHeader(jwtTokenUtils.getHeader());
              if(header != null){
      //            判断是否过期
                  boolean expiration = jwtTokenUtils.isExpiration(header);
                  if(expiration){
                      throw new JwtException("Token过时，请重新获取");
                  }
      //            获取用户名
                  String username = jwtTokenUtils.getUsername(header);
      //          通过 redis   获取用户名的 权限
                  ArrayList<String> o = (ArrayList<String>) redisUtil.get(username);
                  Collection<GrantedAuthority> authority = new ArrayList<>();
                  for( String permissionValue : o) {
                      SimpleGrantedAuthority auth = new SimpleGrantedAuthority(permissionValue);
                      authority.add(auth);
                  }
                  return new UsernamePasswordAuthenticationToken(username,header,authority);
              }
              return  null;
      
          }
      }
      
      ```

   4. 异常处理的 两个处理写到一起了

      ```java
      public class UnAuthEntryPoint implements AuthenticationEntryPoint, AccessDeniedHandler {
          @Override
          public void commence(HttpServletRequest httpServletRequest, HttpServletResponse httpServletResponse, AuthenticationException e) throws IOException, ServletException {
              ResponseUtil.out(httpServletResponse, Result.fail("请登录"));
          }
      
          @Override
          public void handle(HttpServletRequest httpServletRequest, HttpServletResponse httpServletResponse, AccessDeniedException e) throws IOException, ServletException {
              ResponseUtil.out(httpServletResponse, Result.fail(e.getMessage()));
          }
      }
      ```

   5. 添加刚才写过滤器

      ```java
      //                添加重写的过滤器
                      http.addFilter(new TokenAuthFilter(authenticationManager(), jwtTokenUtils, redisUtil)).httpBasic()
      ```

   6. 退出处理器

      ```java
      public class TokenLogoutHandler implements LogoutHandler {
          private TokenManager tokenManager;
          private RedisTemplate redisTemplate;
      
          public TokenLogoutHandler(TokenManager tokenManager,RedisTemplate redisTemplate) {
              this.tokenManager = tokenManager;
              this.redisTemplate = redisTemplate;
          }
          @Override
          public void logout(HttpServletRequest request, HttpServletResponse response, Authentication authentication) {
              //1 从header里面获取token
              //2 token不为空，移除token，从redis删除token
              String token = request.getHeader("token");
              if(token != null) {
                  //移除
                  tokenManager.removeToken(token);
                  //从token获取用户名
                  String username = tokenManager.getUserInfoFromToken(token);
                  redisTemplate.delete(username);
              }
              ResponseUtil.out(response, R.ok());
          }
      }
      ```

   7. 添加

      ```java
      //                添加登出 处理器
                      http.addLogoutHandler(new TokenLogoutHandler(jwtTokenUtils,redisUtil)).and()
      ```