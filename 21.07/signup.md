# 오늘 배운 것
___
* 회원가입

## sign up 
___

데이터 베이스는 몽고db를 사용하였으며, MongoDB의 문서 모델은 개발자가 배우고 사용하기가 쉬우면서도 규모에 관계없이 가장 복잡한 요구사항을 충족시키는 데 필요한 모든 기능을 제공하기 때문에 사용하였다<br/>
회원 가입에 필요한 스키마는 닉네임,비밀번호, 비밀번호 화인이렇게 3가지로 구성하여 회원가입을 하게 하였으며, 각각에 조건을 걸어 조건에 충족되지 않으면 가입이 되지 않게 하였다.<br/>
구성은 라우터를 통해 회원가입을 이뤄지게 하였다.
```
router.post("/users", async (req, res) => {
  const { nickname, password, confirmpassword } = req.body;
  const exists = await User.findOne({ nickname });
  if (exists) {
    res.statusCode = 400;
    res.send(`중복된 닉네임입니다.`);
    return;
  }
  // 닉네임 검증 reg
  if (!/[a-zA-Z0-9]+/.test(nickname) || nickname.length < 3) {
    res.statusCode = 400;
    console.log("회원가입");
    res.send(
      `닉네임은 3자이상, 알파벳 대소문자(a~z, A~Z), 숫자(0~9) 를 포함해야합니다.`
    );
    return;
  }
  // 패스워드 검증
  if (password.includes(nickname) || password.length < 4) {
    res.statusCode = 400;
    res.send(`비밀번호는 4자이상이며 닉네임을 포함하면 안됩니다.`);
    return;
  }
  // 두 패스워다가 같은지 검사
  if (password !== confirmpassword) {
    res.statusCode = 400;
    res.send(`비밀번호가 일치하지 않습니다.`);
    return;
  }
  // 모든 검사가 통과 한 후에
  const user = new User({
    nickname,
    password,
  });
  //유저를 저장, statusCode 성공 리턴
  await user.save();
  res.statusCode = 200;
  res.send();
});
```
서버에서는 위와 같이 조건을 걸어 주었으며, 조건이 충족되지 않으면 status를 이용하여 오류 메시지인 400을 넣어주고 오류메세지를 띄우게 하였다.<br/>

```
function signup_post() {
        const nickname = $('#post_nickname').val();
        const password = $('#post_password').val();
        const confirmpassword = $('#post_confirmpassword').val();
        const data = {
            nickname: nickname,
            password: password,
            confirmpassword: confirmpassword,
        }
        const client = new XMLHttpRequest()
        client.onload = function () {
            if (client.status === 200) {
                alert("회원가입을 축하합니다.")
                location = '/login'
            } else if (client.status === 400) {
                alert(client.responseText);
            }
        }
        client.open('POST', '/api/users');
        client.setRequestHeader('Content-Type', 'application/json');
        client.send(JSON.stringify(data));
 }
 ```
클라이언트에서는 위의 코드는 회원 가입시 클라이언트에서 요구하는 코드를 짠것이다.<br/>
위의 백과 프론트에 요구하는 코드들을 사용하여 회원가입에 필요한 코드를 사용하였고 데이이터는 몽고db로 보내어 회원 정보를 저장하는 식으로 만들었다. 
