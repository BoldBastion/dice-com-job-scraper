[Dice Com Job Scraper](https://apify.com/easyapi/dice-com-job-scraper?fpr=data)

# Dice.com Job Scraper 🎲💼

## 🚀 Effortlessly scrape job listings from Dice.com!

This powerful Actor allows you to extract detailed job information from Dice.com, one of the leading job boards for technology professionals. Whether you're a job seeker, recruiter, or researcher, this tool provides valuable insights into the tech job market.

## 🌟 Key Features

- 📊 Scrape up to 10,000 job listings in one run
- 🔍 Extract comprehensive job details including title, company, location, salary, and more
- 🔄 Automatic pagination handling
- 🛡️ Built-in stealth measures to avoid detection
- ⚡ High-performance scraping with Puppeteer

## 📋 Output Data

For each job listing, the Actor extracts:

- Job ID
- Title
- Company name
- Location
- Posting date
- Salary (if available)
- Employment type
- Job summary
- Detailed page URL
- Company page URL
- Company logo URL
- Remote work availability
- Workplace types
- Easy apply status
- Sponsorship willingness
- Employer type
- Last modified date

## 💡 Use Cases

- Market research on tech job trends
- Competitive analysis for recruiters
- Job search optimization for candidates
- Salary benchmarking
- Tracking company hiring patterns

## 🚦 Getting Started

1. Enter the Dice.com search URL for your desired job category
2. Set the maximum number of results you want to scrape
3. Optionally configure proxy settings for enhanced performance

Let this Actor do the heavy lifting while you focus on analyzing the valuable job market data it provides! 🎉👨‍💻👩‍💻

### Input Example

A full explanation of an input example in JSON.

```
{
    "searchUrl": "https://www.dice.com/jobs?q=ai&countryCode=US&radius=30&radiusUnit=mi&page=1&pageSize=20&language=en",
    "maxResults": 100
}
```

### Output sample

The results will be wrapped into a dataset which you can always find in the **Storage** tab. Here's an excerpt from the data you'd get if you apply the input parameters above:

And here is the same data but in JSON. You can choose in which format to download your data: JSON, JSONL, Excel spreadsheet, HTML table, CSV, or XML.

```
[
	{
		"jobId": "9359a52f3e7274d41bf3d80683216354",
		"title": "Principal AI Engineer",
		"company": "Jobot",
		"location": "Chicago, Illinois, USA",
		"postDate": "2024-10-13T12:22:16Z",
		"salary": "USD 300,000.00 - 350,000.00 per year",
		"jobType": "Full-time",
		"summary": "Hybrid Role  This Jobot Job is hosted by: Duran Workman Are you a fit? Easy Apply now by clicking the \"Apply Now\" button and sending us your resume. Salary: $300,000 - $350,000 per year  A bit about us:  We are seeking a highly skilled and motivated Sr. GenAI Architect to join our team. The ideal candidate will be an expert in developing and implementing AI systems, with a specific focus on generative AI. The successful candidate will be responsible for creating and maintaining scalable, robust ",
		"detailsPageUrl": "https://www.dice.com/job-detail/ddd2e93c-799a-4b0d-82d5-2877f8c5bf22",
		"companyPageUrl": "https://www.dice.com/company/91113390",
		"companyLogoUrl": "https://d3qscgr6xsioh.cloudfront.net/RVkPsbuFScmLFloqItyr_transformed.png?format=webp",
		"workFromHomeAvailability": "FALSE",
		"isRemote": false,
		"workplaceTypes": [
			"On-Site"
		],
		"easyApply": false,
		"willingToSponsor": false,
		"employerType": "Recruiter",
		"modifiedDate": "2024-10-15T00:22:03Z"
	},
	{
		"jobId": "dc653842cdedc78546175daf7fc43329",
		"title": "Founding Applied AI Research Scientist",
		"company": "Jobot",
		"location": "San Francisco, California, USA",
		"postDate": "2024-10-14T12:28:34Z",
		"salary": "USD 180,000.00 - 210,000.00 per year",
		"jobType": "Full-time",
		"summary": "Well-Funded Seed Stage Startup in Generative AI & LLM Space / Remote Flexibility  This Jobot Job is hosted by: Caitlyn Hardy Are you a fit? Easy Apply now by clicking the \"Apply Now\" button and sending us your resume. Salary: $180,000 - $210,000 per year  A bit about us:  We are a well-funded Seed-stage startup that has plans to double our team size in the next 6 months. Our product is public and already generating revenue. This product is unlike anything on the market; it was created for develo",
		"detailsPageUrl": "https://www.dice.com/job-detail/c00ad119-0292-42a8-b672-629fb79f182d",
		"companyPageUrl": "https://www.dice.com/company/91113390",
		"companyLogoUrl": "https://d3qscgr6xsioh.cloudfront.net/RVkPsbuFScmLFloqItyr_transformed.png?format=webp",
		"workFromHomeAvailability": "FALSE",
		"isRemote": false,
		"workplaceTypes": [
			"On-Site"
		],
		"easyApply": false,
		"willingToSponsor": false,
		"employerType": "Recruiter",
		"modifiedDate": "2024-10-15T00:27:30Z"
	},
    ...
]
```