# ๐Git Workflow

Github flow

--------------------------------------------



### โจFeature Branch Workflow

- Shared repository model (์ ์ฅ์์ ์์ ๊ถ์ด ์๋ ๊ฒฝ์ฐ)



#### Workflow

1. ๊ฐ ์ฌ์ฉ์๋ ์๊ฒฉ ์ ์ฅ์์ ์์ ๊ถ์ ๊ฐ์ง ์ํ

   ```markdown
   1๋ฒ ์ ์ , 2๋ฒ ์ ์ , 3๋ฒ ์ ์  Collaborators์ ์ถ๊ฐ
   ```

2. clone์ ํตํด ์ ์ฅ์๋ฅผ ๋ก์ปฌ์ ๋ณต์ 

   ```bash
   git clone <์๊ฒฉ์ ์ฅ์ ์ฃผ์>
   ```

3. ๊ธฐ๋ฅ ์ถ๊ฐ๋ฅผ ์ํด ๊ฐ์ ๋ธ๋์น ์์ฑ ๋ฐ ๊ธฐ๋ฅ ๊ตฌํ 

   - master์์ ๊ตฌํ X, master๋ ๋ณํฉํ  ๋๋ง ์ฌ์ฉ

   ```markdown
   1๋ฒ ์ ์ : feature/login
   2๋ฒ ์ ์ : feature/signup
   3๋ฒ ์ ์ : feature/profile
   ```

   ```bash
   # 1๋ฒ ์ ์ ์ ๊ฒฝ์ฐ
   $ git switch -c feature/login  # ๋ธ๋์น ์์ฑ, ์ด๋
   $ touch login.md  # ๊ธฐ๋ฅ ๊ตฌํ
   $ git add .
   $ git commit -m "login completed"
   ```

4. ๊ธฐ๋ฅ ๊ตฌํ ํ `git push <์๊ฒฉ์ ์ฅ์ ์ด๋ฆ> <๋ธ๋์น ์ด๋ฆ>`

   ```bash
   # ์๊ฒฉ์ ์ฅ์ ์ด๋ฆ์ด origin์ผ ๊ฒฝ์ฐ
   # 1๋ฒ ์ ์ 
   $ git push origin feature/login
   
   # 2๋ฒ ์ ์ 
   $ git push origin feature/signup
   
   # 3๋ฒ ์ ์ 
   $ git push origin feature/profile
   ```

5. Pull Request

   - `Compare & pull request` ๋ฒํผ
   - ์์ฒญ์ ํ๋ฉด Pull requests ๋ชฉ๋ก์ ๋๊ธฐ

6. ๋ณํฉ & ๋ณํฉ ์๋ฃ๋ ๋ธ๋์น ์ญ์ 

   - ์ปค๋ฐ๊ณผ ๋ณ๊ฒฝ๋ ๋ถ๋ถ ํ์ธ ํ `merge` ๋ฒํผ ๋๋ ์๋ชป๋ ๋ถ๋ถ์ด ์๋ค๋ฉด `close` ๋ฒํผ

   - `merge` ๋ฒํผ ํด๋ฆญ ํ `Delete branch` ๋ฒํผ

     โ ์๊ฒฉ ์ ์ฅ์์ master branch ๋ฒ์ ์ ์ด๋, ๊ฐ ์ ์ ์ ๋ก์ปฌ master branch ๋ฒ์ ์ ์ด๋ X

     โ repository์ ์์ ๊ถ์ ๊ฐ์ง ์ ์ ๊ฐ merge ํ ๋ฐ๋์ ๋ชจ๋  ์ ์ ์๊ฒ ์๋ ค์ผ ํจ

7. ๊ฐ ์ ์ ๋ master ๋ธ๋์น๋ก ์ด๋, ๋ณํฉ๋ master์ ๋ด์ฉ์ pull

   ```bash
   $ git switch master
   $ git pull origin master
   ```

8. ๊ฐ ์ ์ ๋ ์๊ฒฉ ์ ์ฅ์์์ ๋ณํฉ ์๋ฃ๋ ๋ก์ปฌ ๋ธ๋์น ์ญ์ 

   ```bash
   $ git branch -d feature/login
   ```





### โจForking Workflow

- Fork & Pull model (์ ์ฅ์์ ์์ ๊ถ์ด ์๋ ๊ฒฝ์ฐ)
- ์คํ์์ค



#### Workflow

1. ์์ ๊ถ์ด ์๋ ์๊ฒฉ์ ์ฅ์๋ฅผ fork๋ฅผ ํตํด ๋ด ์๊ฒฉ์ ์ฅ์๋ก ๋ณต์ 

2. ๋ณต์ ํ ๊ฒ์ clone (์ด๋ ์๊ฒฉ์ ์ฅ์ ์ด๋ฆ์ origin์ผ๋ก ์ค์ ๋จ)

   ```bash
   $ git clone <๋ณต์ ํ ์๊ฒฉ์ ์ฅ์ ์ฃผ์>
   ```

3. ์ถํ ๋ก์ปฌ ์ ์ฅ์๋ฅผ ์๋ณธ ์๊ฒฉ ์ ์ฅ์์ ๋๊ธฐํํ๊ธฐ ์ํด ์๋ณธ์ ๋ํด์๋ URL ์ฐ๊ฒฐ

   - upstream: ์ผ๋ฐ์ ์ผ๋ก ์ง์ ํ๋ ์๋ณธ ์๊ฒฉ์ ์ฅ์ ์ด๋ฆ

   ```bash
   $ git remote add upstream <์๋ณธ ์๊ฒฉ์ ์ฅ์ URL>
   ```

4. ๊ธฐ๋ฅ ์ถ๊ฐ๋ฅผ ์ํด ๋ธ๋์น ์์ฑ ๋ฐ ๊ธฐ๋ฅ ๊ตฌํ

   ```bash
   $ git switch -c feature/login
   $ touch login.md
   $ git add .
   $ git commit -m "fixed login.md"
   ```

5. ๊ธฐ๋ฅ ๊ตฌํ ํ ๋ณต์ ํ ์๊ฒฉ์ ์ฅ์(origin)์ ๋ธ๋์น ๋ฐ์

   - ์๋ณธ ์๊ฒฉ์ ์ฅ์(upstream)์๋ ์์ ๊ถ์ด ์๊ธฐ ๋๋ฌธ์ push ๋ถ๊ฐ๋ฅ

   ```bash
   $ git push origin feature/login
   ```

6. ๋ณต์ ํ ์๊ฒฉ์ ์ฅ์(origin)์์ ์๋ณธ ์๊ฒฉ์ ์ฅ์(upstream)๋ก pull request

   โ ์๋ณธ ์๊ฒฉ์ ์ฅ์์ Pull requests ๋ชฉ๋ก์ ๋๊ธฐ

7. ์๋ณธ ์๊ฒฉ์ ์ฅ์(upstream)์์ ๋ณํฉ์๋ฃ 

   โ ๋ณํฉ ์๋ฃ๋ ๋ณต์  ์๊ฒฉ์ ์ฅ์(origin)์ ๋ธ๋์น ์ญ์ 

   โ ๋ก์ปฌ์์ master ๋ธ๋์น๋ก switch, ์๋ณธ ์๊ฒฉ์ ์ฅ์(upstream)๋ฅผ pull

   ```bash
   $ git switch master
   $ git pull upstream master
   ```

8. ์๊ฒฉ์ ์ฅ์์์ ๋ณํฉ ์๋ฃ๋ ๋ก์ปฌ ๋ธ๋์น ์ญ์ 

   ```bash
   $ git branch -d feature/login
   ```

   