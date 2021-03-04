# Mongoose schema 사용자 정의 메소드!
Mongoose 강의 영상을 보다가 스키마 사용자 정의 메소드 __`statics`__ 와 __`methods`__  키워드를 사용하는데 차이가 궁금해져서 정리함 
     
- MongoDB는 NoSQL 데이터베이스로 문서 지향(Document-Oriented)적인 데이터베이스      
- Mongoose는 MongoDB ODM(Object Document Mapping)인데 객체와 문서를 연결해준다는 뜻     
- Object는 자바스크립트의 객체, Document는 몽고DB의 문서      
- 즉 MongoDB의 Document를 자바스크립트의 객체로 바꾸어주는 역할    
> 여기서 말하는 문서는 RDBMS의 record와 비슷한 개념으로 하나 이상의 key-value 쌍으로 이뤄져있다.

<br>

## 📌statics & methods 키워드

스키마를 통해 만든 인스턴스(userSchema)에서 사용자 정의 메소드를 사용 할 수 있다.   

<br>

```javascript
const { mongoose } = require('mongoose');

const userSchema = new Schema({
      name: {
        type: String,
        maxlength: 50
    },
    email: {
        type: String,
        trim: true,
        unique: 1
    },
    password: {
        type: String,
        minlength: 5
    }
});

userSchema.methods.test1 = function () {}
userSchema.statics.test2 = function () {}

const User = mongoose.model('User', userSchema);

module.exports = { User }


```

<br>

<br>

__`statics`__

- statics의 this는 mongoose 모델을 가리킨다.
- statics는 하나의 Collection(Table) 단위로 사용하는 기능이다.
- mongoose 모델에서 바로 사용이 가능하다.

```javascript
userSchema.statics.findByToken = function (token, cb) {
    const user = this;

    jwt.verify(token,'secret',function(err, decode){
        user.findOne({ "_id":decode, "token":token }, function(err, user) {
            if(err) return cb(err);
            cb(null, user);
        });
    });
}
```

<br>

<br>

__`methods`__

- methods의 this는 호출한 객체를 가리킨다
- methods는 하나의 Document(Record) 단위로 사용하는 기능이다.

```javascript
userSchema.methods.comparePassword = function (plainPassword, cb) {
    bcrypt.compare(plainPassword, this.password, (err, isMatch) => {
       if (err) {
           return cb(err);
       }
       cb(null, isMatch);
    });
}
```

<br>
