# EUREKA 数据结构设计

## 用户

``` json

UserProfile
{
    "userid": "UUID",
    "username": "Name",
    "password": "Password",
    "mobile": "XXXXXXXXXX",
    "im":[
        {"type":"telegram","user":"loginName"},
        {"type":"telegram","user":"loginName"}
    ],
    "city":"Chengdu",
    "rank":[
        {"base": 1 },
        {"understanding": 2 },
        {"speed": 2 },
        {"skill": 3 },
        {"proficiency":2},
        ],              // 从5个维度的考察结果评分
    "role": "S:student T：teacher A：assistant",
    "grand":  "2018-junior/2018-mid/2018-high",
    "school": "成都市第二中学",
    "point":1000,
    "tags":["good skill","slow","good understanding"], //系统给出的标签
    "Token":"GxiXjLXxVpaUZ3u6v7dll1Tt1Q1wY5nUEN77"
}
```

## 课程模版

``` json
CourseTemplate
{
    "courseid":"UUID",
    "title":"Math-Algebra-Function",
    "desciption":"Algebra advanced for highschool",
    "tags":["Hard","easy understanding","Hard point:defination"],
    "type": "基础班/提高班/超前班",
    "status": "opening/expired",
    "details":
    {
        "steps":[
        {
            "Sequnce":1,
            "title":"The Concept",
            "desciption":"Algebra advanced for highschool",
            "datalink":[
                {"Concepts":"https://eureka.com/course/courseid/s1/afasdd.md"},
                {"Practics":"https://eureka.com/course/courseid/s1/math-practics.md"},
                {"test":"https://eureka.com/course/courseid/s1/math-test.md"},
                ],
            "env": "https://zoom.us/j/3268684963"
        },
        {
            "Sequnce":2,
            "title":"The Concept",
            "desciption":"Algebra advanced for highschool",
            "datalink":[
                {"Concepts":"https://eureka.com/course/courseid/s2/afasdd.md"},
                {"Practics":"https://eureka.com/course/courseid/s2/math-practics.md"},
                {"test":"https://eureka.com/course/courseid/s2/math-test.md"},
                ],
            "online_env": "https://zoom.us/j/3268684963"
        }
        ],
        "intro":
        {
            "text":"https://eureka.com/course/courseid/intro.md",
            "imagelink":"https://eureka.com/course/courseid/images/intro.png"
        },
        "finish":
        {
            "text": "https://eureka.com/course/courseid/finish.md",
            "datalink":[
                {"playback1":"https://eureka.com/course/courseid/screen.mp4"},
                {"onlinerecorder":"https://eureka.com/course/courseid/questions.mp4"}
            ],
            "feedback":[
                {
                    "role":"teacher",
                    "uid":"userid",
                    "comments":""
                },
                {
                    "role":"assistant",
                    "uid":"userid",
                    "comments":""
                },
                {
                    "role":"student",
                    "uid":"userid",
                    "comments":""
                }
            ]
        }
    }
}
```

## 课程实例

``` json
CourseInstance
{
    "courseid":"UUID",
    "ctid": "CourseTemplate{id}",
    "starttime":["2018-10-10 20:30:00","2018-10-16 20:30:00"],
    "endtime":["2018-10-10 21:30:00","2018-10-16 22:00:00"],
    "teacher":"userid",
    "assistant":"userid",
    "registrants":
    [
        "studentid","studentid","studentid"
    ],
    "currentstep": 1,
    "status": "open/started/end"
}
```

## 操作日志

``` json
Log
{
    "details":[
        {
            "timestamp":"2018-10-10 21:30:00:000",
            "userid": "user-uuid",
            "action": "Order the course xxxxxxxxxxxx",
            "amt": 1000.00,
            "point":1000
        },
        {
            "timestamp":"2018-10-10 22:30:00:000",
            "userid": "user-uuid",
            "action": "complete the course xxxxxxxxxxxx step 1",
            "amt": 0.00,
            "point":100
        }
    ]
}
```