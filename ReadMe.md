# 💫 Aishwarya Rajan:

Passionate and creative web designer specializing in visually stunning and functional websites. I blend aesthetics with usability to deliver outstanding results. From concept to completion, I bring ideas to life with clean code and attention to detail.


### 💻 Programming language:

![HTML5](https://img.shields.io/badge/html5-%23E34F26.svg?style=for-the-badge&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/css3-%231572B6.svg?style=for-the-badge&logo=css3&logoColor=white) 
![JavaScript](https://img.shields.io/badge/javascript-%23323330.svg?style=for-the-badge&logo=javascript&logoColor=%23F7DF1E)
![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54) 
![Java](https://img.shields.io/badge/java-%23ED8B00.svg?style=for-the-badge&logo=openjdk&logoColor=white)
![R](https://img.shields.io/badge/r-%23276DC3.svg?style=for-the-badge&logo=r&logoColor=white)


### 📀 Designing:
![Canva](https://img.shields.io/badge/Canva-%2300C4CC.svg?style=for-the-badge&logo=Canva&logoColor=white)
![Figma](https://img.shields.io/badge/figma-%23F24E1E.svg?style=for-the-badge&logo=figma&logoColor=white)
![Adobe After Effects](https://img.shields.io/badge/Adobe%20After%20Effects-9999FF.svg?style=for-the-badge&logo=Adobe%20After%20Effects&logoColor=white)
![Adobe Illustrator](https://img.shields.io/badge/adobeillustrator-%23FF9A00.svg?style=for-the-badge&logo=adobeillustrator&logoColor=white)
![Dribbble](https://img.shields.io/badge/Dribbble-EA4C89?style=for-the-badge&logo=dribbble&logoColor=white)


### 🧰 Frameworks:
![NumPy](https://img.shields.io/badge/numpy-%23013243.svg?style=for-the-badge&logo=numpy&logoColor=white)
![Pandas](https://img.shields.io/badge/pandas-%23150458.svg?style=for-the-badge&logo=pandas&logoColor=white)
![Node.js](https://img.shields.io/badge/node.js-%23167458.svg?style=for-the-badge&logo=node.js&logoColor=white)

## 📊 GitHub Stats:

<img align="left" width="47%" src="https://github-readme-stats.vercel.app/api?username=a5hcodes&theme=dracula&show_icons=true&hide_border=true" />

<img align="left" width="48%" src="https://github-readme-stats.vercel.app/api/top-langs/?username=a5hcodes&theme=dracula&layout=compact&hide_border=true" />

https://raw.githubusercontent.com/{a5hcodes}/{a5hcodes}/output/github-contribution-grid-snake-dark.svg
name: generate animation

on:
  # run automatically every 24 hours
  schedule:
    - cron: "0 */12 * * *" 
  
  # allows to manually run the job at any time
  workflow_dispatch:
  
  # run on every push on the main branch
  push:
    branches:
    - main
    
  

jobs:
  generate:
    runs-on: ubuntu-latest
    timeout-minutes: 10
    
    steps:
      # generates a snake game from a github user (<github_user_name>) contributions graph, output a svg animation at <svg_out_path>
      - name: generate github-contribution-grid-snake.svg
        uses: Platane/snk/svg-only@v3
        with:
          github_user_name: ${{ github.a5hcodes }}
          outputs: |
            dist/github-contribution-grid-snake.svg
            dist/github-contribution-grid-snake-dark.svg?palette=github-dark
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
          
          
      # push the content of <build_dir> to a branch
      # the content will be available at https://raw.githubusercontent.com/<github_user>/<repository>/<target_branch>/<file> , or as github page
      - name: push github-contribution-grid-snake.svg to the output branch
        uses: crazy-max/ghaction-github-pages@v3.1.0
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
