# **Looking for a job in a startup?**<br>This is the tool for **u!**
<img align="right" width="300" height="300" src="http://drive.google.com/uc?export=view&id=1HBP2hJQw5vYCouNEqvZGHZggaf-HaMCn">

Do you think Companies read all CVs they receive? No way! They use algorithms to filter the best potential CVs based on keywords that match what they are looking for.  

**Why not do the same, but the other way around?**  
Instead of Companies filtering Candidates' CVs, this tool enables you to ***filter Companies*** based on what's important to **u!**  

**How does it work?**  
**u!** has a database of startups companies and a classification of the most relevant keywords related to each company. Then, you will upload your CV, and the tool will identify what is important to **u!**  
Finally, the tool will identify the startup companies with the best fit with your CV, and draft cover letters designed to each of those companies, personalized with your skills and experiences!  

Give it a shot and good luck with your job hunting!

# (pt) **Procurando emprego em uma startup?**<br> Essa é a ferramenta para você!

Você acha mesmo que as empresas leem todos os CVs que recebem? Claro que não! Elas usam algorítmos para filtrar os melhores CVs baseado em palavras chave que se encaixam no que estão buscando.

**Porque não fazer o mesmo, só que ao contrário?**
Ao invés de Empresas filtrando CVs dos Candidatos, essa ferramenta te permite **filtrar Empresas** baseado no que é importante pra **você**!

**Como funciona?**  
A ferramenta **u!** tem uma base de dados de startups e uma classificação das palavras chave mais relevantes para cada uma dessas empresas. Além disso, você vai fazer o upload do seu currículo, e a ferramenta vai identificar o que é importante pra *você*, baseado nas suas experiências e habilidades.  
Finalmente, a ferramenta identificará quais são as startups que se encaixam melhor com o **seu** perfil, e criará rascunhos de Cover Letters especificamente para cada uma dessas empresas, personalizadas com suas habilidades e experiências!  

Boa sorte com sua busca de emprego!



# **Key steps**  
<img align="right" width="202" height="78" src="http://drive.google.com/uc?export=view&id=1OBzNnh5iDQDDcH4zzVIXO7QQbH90Ta7w">

**Get Startups database from Kaggle**  

This project is using a startups database available in Kaggle (link below).  
The description of each startup will be used to identify keywords.  
https://www.kaggle.com/datasets/joebeachcapital/startups  

<img width="600" height="600" src="http://drive.google.com/uc?export=view&id=1kFCkdQHpZRZnnDLRDLJlpE2bY51Nx1b1">
<br><br>  

**Use Gemini to identify what's important to you based on your CV**

<img width="298" height="110" src="http://drive.google.com/uc?export=view&id=1QnuerEQbhglsvfCtnwLrz_hGugRrsNSg">

```
prompt = f""""
Consider the following curriculum of a professional:
{file_content}

Consider this counter of words/expressions:
{common_items_counter}

List the words/expressions with highest count in the counter that are also relevant in the curriculum.
Return only the words/expressions, without any analysis, in the format: word1, word2, word3, etc.
Only include words/expressions that are relevant in the curriculum.
"""
response = model.generate_content(prompt)
text = response.text
related_keywords = [word.strip() for word in text.split(',')]
print(related_keywords)
```

Example response:  
['data', 'finance', 'system', 'application', 'web', 'mobile', 'software', 'online']
<br><br>  

**Use Gemini to identify startups with best fit, and create personalized Cover Letters**
```
for i in range(min(3, len(df))):  # Limiting to 3 cover letters, due to Gemini restrictions (too many requests)
  company_data = json.dumps(json_list[i])
  prompt = f"""
  Consider the following curriculum of a professional:
  {file_content}

  Consider the following information of a company:
  {company_data}

  Draft a cover letter for the professional to this company, with the objective of
  convincing the company to consider the professional for hiring. Highlight the professional's
  skills and experiences that are most relevant to the company. Emphasize how the professional's
  expertise can contribute to the company.
  Do not include header or contact information.
  """
  response = model.generate_content(prompt)
  print(response.text)
```

Example response:  
## Cover Letter Draft

Dear MessageParty Hiring Team,

I am writing to express my keen interest in joining MessageParty, a company at the forefront of mobile content creation and consumption. With my extensive experience in finance, data analytics, and cross-functional leadership, coupled with my passion for technology and innovation, I am confident I can make a significant contribution to your team.

My career at Procter & Gamble has equipped me with a diverse skillset directly applicable to MessageParty's dynamic environment. In my recent roles, I spearheaded initiatives that drove revenue growth, optimized profitability, and mitigated risk across various business units, including e-commerce – a channel exhibiting remarkable parallels to your mobile platform.  

My ability to analyze complex data sets and translate them into actionable insights would be invaluable to MessageParty.  I developed a Power BI tool that consolidated data from multiple sources, saving time and enabling faster, data-driven decision-making.  This experience, along with my Python skills and data science projects, demonstrates my ability to leverage data for strategic advantage.

Furthermore, my leadership experience in cross-functional teams, including marketing and sales, aligns perfectly with the collaborative nature of MessageParty's platform. I have a proven track record of orchestrating successful projects, optimizing budget allocation, and achieving ambitious goals.

I am particularly excited about MessageParty's focus on mobile technology and its potential to revolutionize content creation and consumption. My passion for this field is evident in my personal projects, such as analyzing and visualizing data related to Star Wars and the Beatles. 

I am confident that my skills and experience, combined with my enthusiasm for MessageParty's mission, make me a strong candidate for your team. I am eager to learn more about this opportunity and discuss how I can contribute to MessageParty's continued success.

Thank you for your time and consideration.

Sincerely,

Andre Sepulveda Villela 

## Cover Letter Draft for Errplane

Dear Hiring Manager,

I am writing to express my keen interest in joining Errplane and contributing to your mission of enabling users to monitor the performance, uptime, and errors of web applications. With over 14 years of experience in finance and data analytics, coupled with my recent foray into data science, I am confident I possess the skills and expertise to significantly impact your team.

My career at Procter & Gamble has equipped me with a diverse skillset that aligns well with Errplane's needs. In my current role as Senior Finance Manager, I spearheaded cost-saving initiatives through competitive benchmarking and risk mitigation strategies, demonstrating my analytical prowess and ability to translate data into actionable insights.  Furthermore, my experience in developing a Power BI tool that consolidated multiple data sources, saving significant time and resources, directly translates to the data-driven environment at Errplane.

My passion for data analysis extends beyond my professional experience. I have actively pursued data science projects, utilizing Python, Pandas, and Matplotlib to analyze and visualize data from various sources. These projects, available on my GitHub profile, showcase my ability to extract meaningful insights from complex datasets – a skill that would be invaluable in understanding and improving web application performance.

I am particularly excited about Errplane's focus on software solutions for monitoring web applications. My experience in e-commerce finance, where I headed the financial strategy for the fastest-growing channel and achieved significant revenue growth, demonstrates my understanding of the digital landscape and the importance of robust web applications. 

I am confident that my combined experience in finance, data analysis, and data science, along with my proven ability to drive growth and efficiency, would make me a valuable asset to Errplane. I am eager to learn more about this opportunity and discuss how my skills can contribute to your continued success.

Thank you for your time and consideration.

Sincerely,

Andre Sepulveda Villela 

## Cover Letter for TradeBlock

Dear Hiring Manager,

I am writing to express my keen interest in joining TradeBlock, a leader in digital currency data and analysis. With my extensive experience in finance, data analytics, and a growing passion for the cryptocurrency space, I am confident I can make significant contributions to your team.

My 14-year tenure at Procter & Gamble has equipped me with a diverse skillset highly relevant to TradeBlock's mission. As a Senior Finance Manager, I consistently spearheaded initiatives that drove revenue growth, improved profitability, and mitigated risk across various sectors like e-commerce, supply chain, and sales. My ability to analyze complex data, identify trends, and translate them into actionable insights was instrumental in achieving these successes. 

I am particularly excited about the opportunity to leverage my data analytics expertise within the digital currency domain. My recent completion of a Data Science Certificate, coupled with personal projects analyzing Star Wars and Beatles data using Python, demonstrates my commitment to continuous learning and applying data science tools.  

Furthermore, my experience in developing a Power BI tool that consolidated multiple data sources at P&G directly translates to the needs of TradeBlock. This, combined with my proficiency in MS Office and SAP, ensures I can seamlessly integrate into your data-driven environment.

I am confident that my passion for financial analysis, data-driven decision making, and the burgeoning cryptocurrency landscape makes me an ideal candidate for TradeBlock. I am eager to learn more about your current projects and discuss how my skills and experience can contribute to your continued success.

Thank you for your time and consideration.

Sincerely,

Andre Sepulveda Villela 
