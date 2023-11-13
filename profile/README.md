
  
# TenQuest: 익명 질문 소통 플랫폼
추천 질문지 또는 나만의 질문지를 생성하여 공유하고, 해당 링크를 통해 다른 사용자들이 익명으로 질문에 대한 답변을 남겨주는 서비스이다.

<br/>

## Demo
페이지별 움짤 + 설명


<br/>

## System Architecture
<img width="500" alt="system architecture" src="https://github.com/TenQuest-Team/.github/assets/70912819/f1f93a1e-2b72-4b4b-8786-38f0ac08c53b">



<br/>

## Backend API
<img width="810" alt="API 설계" src="https://github.com/TenQuest-Team/.github/assets/70912819/bbb775fe-d787-4997-aaa1-e96deb95dd83">




<br/>



## Tech Stack
<table>
  <tbody>
    <tr>
      <th align="center">Frontend</th>
      <th align="center">Backend</th>
      <th align="center">DevOps</th>
      <th align="center">Etc</th>
    </tr>
    <tr>
      <td align="center"> 
        <img src="https://img.shields.io/badge/JAVASCRIPT-F7DF1E?style=flat&logo=JAVASCRIPT&logoColor=white" />
      </td>
      <td align="center">
        <img src="https://img.shields.io/badge/JAVA-007396?style=flat&logo=Java&logoColor=white"> 
        <br />
        <img src="https://img.shields.io/badge/SPRING BOOT-6DB33F?style=flat&logo=SPRING BOOT&logoColor=white" />
        <br />
        <img src="https://img.shields.io/badge/SPRING SECURITY-6DB33F?style=flat&logo=SPRING SECURITY&logoColor=white" />
        <br />
        <img src="https://img.shields.io/badge/MYSQL-4479A1?style=flat&logo=MYSQL&logoColor=white" />
      </td>
      <td align="center">
        <img src="https://img.shields.io/badge/GOORM-000000?style=flat&logoColor=white" />
      </td>
      <td align="center">
        <img src="https://img.shields.io/badge/POSTMAN-FF6C37?style=flat&logo=POSTMAN&logoColor=white" />
        <br />
        <img src="https://img.shields.io/badge/GIT-F05032?style=flat&logo=GIT&logoColor=white" />
        <br />
        <img src="https://img.shields.io/badge/FIGMA-F24E1E?style=flat&logo=FIGMA&logoColor=white" />
        <br />
        <img src="https://img.shields.io/badge/NOTION-000000?style=flat&logo=Notion&logoColor=white" />
      </td>
    </tr>
  </tbody>
</table>


<br/>

## How to Start
### 1. Clone Repository
```markdown
$ git clone https://github.com/TenQuest-Team/TenQuest-BE.git
$ git clone https://github.com/TenQuest-Team/TenQuest-Frontend.git
```

### 2. Local execution - Backend
```markdown
$ ./gradlew build && nohup java -jar ./build/libs/*.jar &
```

### 3. Install Packages - Frontend
```markdown
$ cd ../frontend
$ npm install
```

### 4. change API Endpoint - Frontend
```markdown
/frontend/src/api.js

const API_END_POINT = 'https://tenquest.run.goorm.site';
-> const API_END_POINT = 'backend local server';

ctrl+s
```

### 5. Local execution - Frontend
```markdown
$ npm run dev
```




<br/>

## **URL**
- / → Login Page
- /findID -> Find ID Page
- /findPW -> Find Password Page
- /signUp -> Sign Up Page
- /templates -> Template List Page
- /template/preset -> Preset Template List Page
- /createNewTemplate -> Creating Template Page
- /template/{templateId} -> View Answers Page
- /view/question/{templateDocId}/{questionId} -> View Answers By Question Page
- /view/answer/{replyerId} -> View Answers By Answer Page
- /shareTemplate -> Sharing Template Page
- /reply/{templateId} -> Questionnaire Page
- /submitAnswer/{templateId} -> Finished Submit Answer Page


<br/>

## Team
<table>
  <tbody>
    <tr width='100%'>
      <th align="center" width='14%'>구건모</th>
      <th align="center" width='14%'>신성희</th>
      <th align="center" width='14%'>손정원</th>
      <th align="center" width='14%'>김예빈</th>
    </tr>
    <tr>
      <td align="center"><img width="100" alt="image" src="https://github.com/TenQuest-Team/.github/assets/84436996/8e0edbb1-2c03-482f-a945-7ee455885da5"></td>
      <td align='center'><img width="100" alt="image" src="">
</td>
      <td align='center'><img width="100" alt="image" src="">
</td>
      <td align='center'><img width="100" alt="image" src="https://github.com/2023-Summer-Bootcamp-TeamD/.github/assets/70912819/9a9bc664-2e25-4992-a1df-62371430bc4c">
</td>
    </tr>
    <tr>
      <td>Team Leader<br/>Backend<br />DevOps</td>
      <td>Backend</td>
      <td>Backend</td>
      <td>Frontend</td>
    </tr>
    <tr>
      <td width="150"><a href="https://github.com/woody35545">@woody35545</a></td>
      <td width="150"><a href="https://github.com/Shsin9797">@Shsin9797</a></td>
      <td width="150"><a href="https://github.com/songarden">@songarden</a></td>
      <td width="150"><a href="https://github.com/Kimyebin00">@Kimyebin00</a></td>
    </tr>
  </tbody>
</table>

