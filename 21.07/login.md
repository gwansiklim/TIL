# 오늘의 배운 것 
___

* 로그인 (login)

## login
___

로그인은 회원가입시에 사용한 몽고db에서 user정보를 가져와 해당 사이트의 토큰을 주며 로그인이 되는 방식을 구현하였다.<br/>
바로 코드로 넘어 가겠다. 이번 로그인도 라우터를 통해 get요청을 하여 가져오는 방식으로 했다.

```
router.post("/login", async (req, res) => {
  try {
    const { nickname, password } = await postloginSchema.validateAsync(
      req.body
    );
    const user = await User.findOne({ $and: [{ nickname }, { password }] });
    console.log(user);
    if (!user) {
      res.status(400).send({
        errorMessage: "이메일 또는 패스워드가 잘못되었습니다.",
      });
      return;
    }
    const token = jwt.sign({ userId: user._id }, "token password");
    res.send({
      token,
    });
  } catch (err) {
    console.log(err);
    res.status(400).send({
      errorMessage: "요청한 정보가 올바르지 않습니다.",
    });
  }
});
```
위 코드는 백앤드 서버에서 정보를 보내줄때 사용 한 코드이다.

```
    function logininput() {
        let nickname = $("#gologin").val();
        let password = $("#gopassword").val()
        $.ajax({
            type: "POST",
            url: "/api/login",
            data: {
                nickname:nickname,
                password: password,
            },
            success: function (response) {
                if (response["errorMessage"]) {
                    alert(response["errorMessage"])
                    return;
                }
                localStorage.setItem("token", response.token);
                window.location.href="/";
            }
        })
    }
```
위의 코드는 프론트에서 회원 정보를 가져올 때 ajax를 통해 회원 정보를 요구하는 방식으로 사용했다.

위의 2개의 코드를 보는 봐와 같이 로그인시 유저에 대한 정보가 없으면 오류메세지를 띄우게 했으며, 만약 로그인이 성공했으면 로그인 성공한 아이디에 토큰을 뿌련주는 방식을 이용해
해당사이트의 토큰이 없을 경우 해당 사이트 몇몇 기능을 이용할 수 없게 만들었다.
