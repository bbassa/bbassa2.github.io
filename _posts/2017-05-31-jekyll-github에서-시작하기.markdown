---
title: Jekyll quick start on GitHub Pages
layout: post
category: blog
tags: [blog, jekyll, start]
---
## Step 1 : Repository 만들기
> username.github.io

## Step 2 : Repository Clone하기
```bash
git clone https://github.com/username/username.github.io
```

## Step 3 : Settings 에서 Theme 선택
> Tools > Command Pallete - Ctrl+Shift+P

## Step 4 : Sublime Text 3 에 Jekyll 플러그인 설치
> Project > Save Project As 로 저장
> Proejct > Edit Project

```json
{
	"folders":
	[
		{
			"path": "repetentia.github.io"
		}
	],
    "settings":
    {
        "Jekyll":
        {
            "jekyll_posts_path": "absolute_path\\_posts",
            "jekyll_drafts_path": "absolute_path\\_drafts",
            "jekyll_uploads_path": "absolute_path\\uploads",
            "jekyll_templates_path": "absolute_path\\_templates"
        }
    }
}

```

## Step 5 : 새로운 post 작성
 우클릭 (컨텍스트 메뉴)
 > Jekyll > New Post

## Step 6 : GitHub에 반영하기
```bash
git add --all
git commit -m "Messages to leave"
git push -u origin master
```

