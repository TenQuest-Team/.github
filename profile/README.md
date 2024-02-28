
  
# Ten Quest: 익명 질문 소통 플랫폼
추천 질문지 또는 나만의 질문지를 생성하여 공유하고, 해당 링크를 통해 다른 사용자들이 익명으로 질문에 대한 답변을 남겨주는 서비스이다.

<br/>

## Demo

### 질문자 입장에서의 서비스 이용
<table>
  <tr>
    <th align="center" width='350px'>
      나만의 질문지 생성하기
    </th>
    <th align="center" width='350px'>
      추천 템플릿으로 질문지 생성하기
    </th>
  </tr>
  <tr>
    <td align="center" width='350px'>
      <img src='https://github.com/TenQuest-Team/.github/assets/70912819/64caac07-daff-467c-9fe9-1e926069424a' />
    </td>
    <td align="center" width='350px'>
      <img src='https://github.com/TenQuest-Team/.github/assets/70912819/c6de43d1-0aed-46bc-8339-32cc83f13086' />
    </td>
  </tr>
  <tr>
    <td align="center" width='350px'>
      사용자는 여러 카테고리의 예시 질문 중 선택하거나, 직접 질문을 작성해서 최대 10개의 질문을 담은 나만의 질문지를 생성하여 공유할 수 있다.
    </td>
    <td align="center" width='350px'>
      사용자는 아이스브레이킹과 같이 특정한 상황에 맞추어 추천 질문을 미리 담아놓은 템플릿을 통해 간편하게 질문지를 생성하여 공유할 수 있다.
    </td>
  </tr>
</table>

### 답변자 입장에서의 서비스 이용
<table>
  <tr>
    <th align="center" width='350px'>
      질문지에 익명으로 답변하기
    </th>
    <th align="center" width='350px'>
      다른 사용자의 답변 확인하기
    </th>
  </tr>
  <tr>
    <td align="center" width='350px'>
      <img src='https://github.com/TenQuest-Team/.github/assets/70912819/2c8ffc16-02c4-47ab-b288-6a4fa033071f' />
    </td>
    <td align="center" width='350px'>
      <img src='https://github.com/TenQuest-Team/.github/assets/70912819/b1b46339-6e2c-4df3-b83f-e74e091f31cf' />
    </td>
  </tr>
  <tr>
    <td align="center" width='350px'>
      질문지 링크에 접속한 사용자는 익명으로 질문지에 답변을 남길 수 있다.
    </td>
    <td align="center" width='350px'>
      질문지에 답변을 남긴 후 사용자는 다른 사용자들이 남긴 답변들을 구경할 수 있다.
    </td>
  </tr>
</table>


<br/>

## System Architecture
<img width="500" alt="system architecture" src="https://github.com/TenQuest-Team/.github/assets/70912819/f1f93a1e-2b72-4b4b-8786-38f0ac08c53b">


<br />

## ERD

```mermaid
erDiagram
  member_table{
        VARCHAR member_id PK "회원 식별자"
        VARCHAR user_id "아이디"
        VARCHAR user_info "비밀번호"
        VARCHAR user_name "이름"
        VARCHAR user_email "이메일"
        VARCHAR user_roles "권한"
    }

  member_table || -- o{ template_table : "Member(1):Template(0..N)"
    
	template_table{
      VARCHAR template_id PK "템플릿 식별자"
			VARCHAR teamplate_owner FK "소유자의 회원 식별자"
			VARCHAR template_name "템플릿명"
			TIMESTAMP created_at "생성 시간" 
			TINYINT is_public "공개 여부"
}
  template_doc_table || -- |{ template_table : "TemplateDoc(N):Template(1)"
	template_doc_table{
		INT template_doc_id PK "템플릿 도큐먼트 식별자"
		VARCHAR template_id FK "템플릿 식별자"
		VARCHAR question_id FK "질문 식별자"
		INT question_order "질문 순서" 
	}
	
	preset_table{
		VARCHAR preset_id PK "프리셋 식별자"
		VARCHAR preset_name "프리셋명"
	}

	preset_doc_table }| -- || preset_table : "PresetDoc(N):Preset(1)"
	%% `PresetDoc`은 하나의 Preset을 이루는 항목이다.
	preset_doc_table{
		VARCHAR preset_doc_id PK "프리셋 도큐먼트 식별자"
		VARCHAR	preset_id FK "도큐먼트가 속한 프리셋 식별자"
		VARCHAR	question_id "프리셋 도큐먼트에 대한 질문 식별자"
		INT question_order "질문 순서"
	}

	replyer_table{
		VARCHAR replyer_id PK "답변자의 식별자"
		VARCHAR replyer_name FK "답변자의 닉네임"
	}


	answer_table || -- || replyer_table : "Answer(1):Replyer(1)"
	answer_table || -- || template_doc_table : "Answer(1):TemplateDoc(1)"
	answer_table{
		VARCHAR answer_id PK "답변 식별자"
		VARCHAR replyer_id FK "답변자 식별자"
		INT doc_id FK "답변한 템플릿 도큐먼트 식별자"
		VARCHAR answer_content "답변 식별자"
		TINYINT is_public "답변 공개 여부"
		TIMESTAMP answer_time "답변 생성 시간"
	}


	question_table }o -- || member_table : "Question(0..N):Member(1)"
	
	question_table{
		VARCHAR question_id PK "질문 식별자"
		VARCHAR question_content "내용"
		INT question_category_id "질문 카테고리"
		VARCHAR question_created_by FK "질문을 생성한 회원 식별자"
	}

```


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
        <br />
        <img src="https://img.shields.io/badge/NGINX-009639?style=flat&logo=NGINX&logoColor=white" /></td>
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
      <td align='center'><img width="100" alt="image" src="https://github.com/TenQuest-Team/.github/assets/102501352/b07280ca-8e7c-4695-a6b5-eb9bd7a859fe">
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

