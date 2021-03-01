# authing-go-sdk

## What is Authing

[Authing](https://authing.cn/) is an IDaaS which is created by Ivy.

## Installation
Make sure you have a working Go environment. To install `authing-go-sdk`, simply run:

```shell
go get github.com/Authing/graphql
```

## Quick Guide

```go
package main

import (
	"encoding/json"
	"fmt"
	"log"
	"os"
	"regexp"

	authing "github.com/Authing/authing-go-sdk"
	prettyjson "github.com/hokaccha/go-prettyjson"
	"github.com/kelvinji2009/graphql"
)

const (
	clientID  = "5adb75e03055230001023b26"
	appSecret = "e683d18f9d597317d43d7a6522615b9d"
)

func main() {
    // ---User Endpoint
	client := authing.NewClient(clientID, appSecret, false)
	// Enable debug info for graphql client, just comment it if you want to disable the debug info
	client.Client.Log = func(s string) {
		b := []byte(s)
		pj, _ := prettyjson.Format(b)
		fmt.Println(string(pj))
	}

	// >>>Graphql Mutation: register
	input := authing.UserRegisterInput{
		Email:            graphql.String("kelvinji2009@gmail.com"),
		Password:         graphql.String("password"),
		RegisterInClient: graphql.String(clientID),
	}

	m, err := client.Register(&input)
	if err != nil {
		log.Println(">>>>Register failed: " + err.Error())
	} else {
		printJSON(m)
	}

    // ---OAuth Endpoint
	oauthClient := authing.NewOauthClient(clientID, appSecret, false)
	// Enable debug info for graphql client, just comment it if you want to disable the debug info
	oauthClient.Client.Log = func(s string) {
		b := []byte(s)
		pj, _ := prettyjson.Format(b)
		fmt.Println(string(pj))
	}

	// >>>>Graphql Query: Read OAuth List
	readOauthListQueryParameter := authing.ReadOauthListQueryParameter{
		ClientID:   graphql.String(clientID),
		DontGetURL: graphql.Boolean(false),
	}

	q, err := oauthClient.ReadOauthList(&readOauthListQueryParameter)
	if err != nil {
		log.Println(">>>>Read OAuth List failed: " + err.Error())
	} else {
		printJSON(q)
	}

}

// printJSON prints v as JSON encoded with indent to stdout. It panics on any error.
func printJSON(v interface{}) {
	w := json.NewEncoder(os.Stdout)
	w.SetIndent("", "\t")
	err := w.Encode(v)
	if err != nil {
		panic(err)
	}
}
```

## Usages And Examples

### Precondition
1. Please register `Authing` account on the official site.[Authing Register/Login](https://authing.cn/login)
2. Read the official developer document.[Authing Developer Docs](https://docs.authing.cn/#/)
3. Create new application following the guide and save the `clientID` and `appSecert` from the *Dashboard*.[Create New Application](https://authing.cn/dashboard)

### User Endpoint

Please create a user endpoint client first.Then you can do a series of operations for user.

```go
client := authing.NewClient(clientID, appSecret, false)
// Enable debug info for graphql client, just comment it if you want to disable the debug info
client.Client.Log = func(s string) { log.Println(s) }
```

#### Register a new user

```go
input := authing.UserRegisterInput{
	Email:            graphql.String("kelvinji2009@gmail.com"),
	Password:         graphql.String("password"),
	RegisterInClient: graphql.String(clientID),
}

m, err := client.Register(&input)
if err != nil {
	log.Println(">>>>Register failed: " + err.Error())
} else {
	printJSON(m)
}
```

#### User Login

```go
loginInput := authing.UserLoginInput{
	Email:            graphql.String("kelvinji2009@gmail.com"),
	Password:         graphql.String("password!"),
	RegisterInClient: graphql.String(clientID),
}

m, err := client.Login(&loginInput)
if err != nil {
	log.Println(">>>>Login failed: " + err.Error())
} else {
	printJSON(m)
}

userID := string(m.Login.ID) 
```

#### Check Login Status

```go
q, err := client.CheckLoginStatus()
if err != nil {
	log.Println(">>>>Check login status failed: " + err.Error())
} else {
	printJSON(q)
}
```

#### Query User Information

```go
p := authing.UserQueryParameter{
	ID:               graphql.String("5ae3d830f0db4b000117a95e"),
	RegisterInClient: graphql.String(clientID),
}

q, err := client.User(&p)
if err != nil {
	log.Println(">>>>Query user failed: " + err.Error())
} else {
	printJSON(q)
}
```

#### Query All Users

```go
p := authing.UsersQueryParameter{
	RegisterInClient: graphql.String(clientID),
	Page:             graphql.Int(1),
	Count:            graphql.Int(10),
}

q, err := client.Users(&p)
if err != nil {
	log.Println(">>>>Query users failed: " + err.Error())
} else {
	printJSON(q)
}
```

#### Remove User(s)

```go
removeUsersInput := authing.RemoveUsersInput{
	IDs:              []graphql.String{"111", "222"}, // NOTE: Please use your real user IDs
	RegisterInClient: graphql.String(clientID),
	// Operator should be your `Authing.cn` account ID
	// Operator:         graphql.String("5adb75be3055230001023b20"), // no more needed
}

// UserID Validation
for i, id := range removeUsersInput.IDs {
	re := regexp.MustCompile("^[0-9a-fA-F]{24}$")

	if !re.MatchString(string(id)) {
		log.Fatalf(">>>> user ID is invalid ,index: %d, id: %s", i, id)
	}
}

m, err := client.RemoveUsers(&removeUsersInput)
if err != nil {
	log.Println(">>>>Remove users failed: " + err.Error())
} else {
	printJSON(m)
}
```

#### Update User Information

```go
userUpdateInput := authing.UserUpdateInput{
	ID:               graphql.String("5ae3d830f0db4b000117a95e"), // Mandotory in struct
	Username:         graphql.String("kelvinji2009x"),
	Nickname:         graphql.String("Sicario13th"),
	Phone:            graphql.String("18665308994"),
	RegisterInClient: graphql.String(clientID),
}

m, err := client.UpdateUser(&userUpdateInput)
if err != nil {
	log.Println(">>>>Update user failed: " + err.Error())
} else {
	printJSON(m)
}
```

#### Send Verify Email

```go
sendVerifyEmailInput := authing.SendVerifyEmailInput{
	Email:  graphql.String("kelvinji2009@gmail.com"),
	Client: graphql.String(clientID),
}

err := client.SendVerifyEmail(&sendVerifyEmailInput)
if err != nil {
	log.Println(">>>>Send verify email failed: " + err.Error())
}
```

#### Send Reset Password Email

```go
sendResetPasswordEmailInput := authing.SendResetPasswordEmailInput{
	Client: graphql.String(clientID),
	Email:  graphql.String("kelvinji2009@gmail.com"),
}

err := client.SendResetPasswordEmail(&sendResetPasswordEmailInput)
if err != nil {
	log.Println(">>>>Send reset password email failed: " + err.Error())
}
```

#### Verify Reset Password Verify-Code

```go
verifyResetPasswordVerifyCodeInput := authing.VerifyResetPasswordVerifyCodeInput{
	Client:     graphql.String(clientID),
	Email:      graphql.String("kelvinji2009@gmail.com"),
	VerifyCode: graphql.String("7670"),
}

err := client.VerifyResetPasswordVerifyCode(&verifyResetPasswordVerifyCodeInput)
if err != nil {
	log.Println(">>>>Verify reset passwod verify code failed: " + err.Error())
}
```

#### Change Password

```go
changePasswordInput := authing.ChangePasswordInput{
	Client:     graphql.String(clientID),
	Email:      graphql.String("kelvinji2009@gmail.com"),
	VerifyCode: graphql.String("7670"),
	Password:   graphql.String("password!"),
}

err := client.ChangePassword(&changePasswordInput)
if err != nil {
	log.Println(">>>>Change password failed: " + err.Error())
}
```

### OAuth Endpoint

Please create an oauth endpoint client first.

```go
oauthClient := authing.NewOauthClient(clientID, appSecret, false)
// Enable debug info for graphql client, just comment it if you want to disable the debug info
oauthClient.Client.Log = func(s string) { log.Println(s) }
```

#### Read OAuth List

```go
readOauthListQueryParameter := authing.ReadOauthListQueryParameter{
	ClientID:   graphql.String(clientID),
	DontGetURL: graphql.Boolean(false),
}

q, err := oauthClient.ReadOauthList(&readOauthListQueryParameter)
if err != nil {
	log.Println(">>>>Read OAuth List failed: " + err.Error())
} else {
	printJSON(q)
}
```

## TODO

- [ ] More detailed API usages and documents
- [ ] Travis CI support


## Thanks
[Go GraphQL Client](https://github.com/shurcooL/graphql)

[Simple low-level GraphQL HTTP client for Go](https://github.com/machinebox/graphql)



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)