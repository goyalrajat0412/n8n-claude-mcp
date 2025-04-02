# n8n + Claude Integration: Use Cases and Examples

This document showcases practical use cases and examples for integrating n8n with Claude.

## Customer Service Automation

### Ticket Classification and Routing

**Workflow**: 
1. Email trigger node collects incoming support emails
2. Claude analyzes the content to determine:
   - Priority level
   - Department (billing, technical, etc.)
   - Sentiment
3. Tickets are automatically routed to appropriate teams
4. Priority tickets trigger alerts

**Benefits**:
- Reduces manual triage time by 70%
- Ensures consistent categorization
- Improves response times

**Example Prompt**:
```
Analyze the following customer email and provide:
1. Priority (Low/Medium/High)
2. Department (Billing/Technical/Account Management/General)
3. Sentiment (Positive/Neutral/Negative)
4. Brief summary (25 words max)

Return the result as a JSON object.

EMAIL:
{{$json.emailBody}}
```

### AI-Assisted Response Generation

**Workflow**:
1. Support agent selects a ticket
2. Claude analyzes ticket history and customer profile
3. Claude suggests personalized response templates
4. Agent reviews, edits, and sends the response

**Benefits**:
- Reduces response drafting time by 50%
- Maintains consistent voice and quality
- Provides contextually relevant solutions

## Content Creation and Management

### Automated Content Creation

**Workflow**:
1. Content calendar triggers creation tasks
2. Claude generates first drafts based on topic briefs
3. Drafts are sent to editors for review
4. Approved content is scheduled for publication

**Example Prompt**:
```
Create a blog post about {topic} with the following specifications:
- Target audience: {audience}
- Word count: approximately 800 words
- Key points to include: {points}
- Tone: {tone}
- Include a compelling headline, introduction, and conclusion

Format with proper Markdown headings and structure.
```

### Content Repurposing

**Workflow**:
1. Long-form content is uploaded
2. Claude extracts key points and insights
3. Content is reformatted for different platforms:
   - Social media posts
   - Email newsletters
   - Video scripts
   - Infographic text

**Benefits**:
- Maximizes content ROI
- Ensures consistent messaging across channels
- Reduces manual reformatting time

## Data Analysis and Reporting

### Intelligent Data Summarization

**Workflow**:
1. Database query retrieves business metrics
2. Claude analyzes trends and patterns
3. Natural language reports are generated
4. Reports are distributed to stakeholders

**Example Implementation**:
```
SELECT * FROM monthly_sales WHERE date BETWEEN {{$json.startDate}} AND {{$json.endDate}}
```

Pass to Claude with:
```
Analyze the following sales data and provide:
1. A summary of overall performance
2. Key trends and patterns
3. Notable outliers or anomalies
4. Actionable recommendations

Include relevant metrics and percentages to support your analysis.

DATA:
{{$json.salesData}}
```

### Automated Competitive Analysis

**Workflow**:
1. Web scraping nodes collect competitor content
2. Claude analyzes positioning, messaging, and offers
3. Comparative analysis is generated
4. Strategic recommendations are provided

**Benefits**:
- Keeps competitive intelligence up-to-date
- Provides actionable insights
- Reduces manual research time

## Document Processing

### Intelligent Document Extraction

**Workflow**:
1. PDF documents are uploaded to a designated folder
2. Documents are processed using Document Loader nodes
3. Claude extracts specific information (contracts, invoices, etc.)
4. Extracted data is stored in a database

**Example Prompt**:
```
Extract the following information from this contract:

1. Parties involved (names and addresses)
2. Contract start and end dates
3. Payment terms
4. Key deliverables
5. Termination conditions

Format the extracted information as a JSON object.

DOCUMENT:
{{$json.documentText}}
```

### Document Summarization and QA

**Workflow**:
1. Large documents are chunked and stored in vector database
2. Users submit questions through a form
3. Relevant chunks are retrieved
4. Claude answers the question using the retrieved context

**Benefits**:
- Makes document knowledge accessible
- Reduces time spent searching for information
- Provides consistent answers across teams

## Social Media Management

### AI-Powered Content Moderation

**Workflow**:
1. Social comments are collected via platform APIs
2. Claude reviews comments for policy violations
3. Problematic content is flagged for review
4. Safe comments are automatically approved

**Example Prompt**:
```
Review the following social media comment and determine if it violates our community guidelines:

1. Contains hate speech or discrimination
2. Contains threats or incites violence
3. Contains obscene or inappropriate content
4. Contains spam or misleading information
5. Contains personal attacks

Return a single JSON object with:
- violation: true/false
- categories: array of violated categories
- confidence: number between 0-1
- recommendation: "approve", "review", or "reject"

COMMENT:
{{$json.commentText}}
```

### Scheduled Content Creation

**Workflow**:
1. Content calendar defines posting schedule
2. Claude generates appropriate content for each platform
3. Content is scheduled for posting
4. Performance metrics are collected and analyzed

**Benefits**:
- Maintains consistent posting schedule
- Optimizes content for each platform
- Reduces manual content creation time

## Product Development

### User Feedback Analysis

**Workflow**:
1. User feedback is collected from multiple channels
2. Claude categorizes and analyzes feedback
3. Key insights and patterns are identified
4. Product teams receive structured reports

**Example Prompt**:
```
Analyze the following collection of user feedback and:
1. Categorize each feedback item (Bug, Feature Request, UX Issue, Performance, etc.)
2. Identify recurring themes or patterns
3. Highlight high-impact issues based on frequency and severity
4. Provide a summary of key insights with actionable recommendations

USER FEEDBACK:
{{$json.feedbackCollection}}
```

### Feature Specification Generation

**Workflow**:
1. Product managers input feature concepts
2. Claude helps expand ideas into detailed specifications
3. Technical requirements and acceptance criteria are generated
4. Specs are reviewed and refined for development

**Benefits**:
- Accelerates specification process
- Ensures comprehensive coverage of requirements
- Maintains consistent documentation format

## HR and Recruitment

### Resume Screening and Matching

**Workflow**:
1. Job descriptions are stored in a database
2. Resumes are uploaded to an applicant tracking system
3. Claude compares resumes to job requirements
4. Candidates are scored and ranked

**Example Prompt**:
```
Compare the following resume to the job description and provide:
1. Overall match score (0-100)
2. Matching skills and experiences
3. Notable gaps or missing requirements
4. Suggested interview questions based on the candidate's background

JOB DESCRIPTION:
{{$json.jobDescription}}

RESUME:
{{$json.resumeText}}
```

### Interview Question Generation

**Workflow**:
1. Job details and candidate information are input
2. Claude generates tailored interview questions
3. Questions focus on relevant skills and experience
4. Interviewers receive question packages before meetings

**Benefits**:
- Ensures consistent evaluation criteria
- Personalizes assessment to candidate background
- Improves interview preparation

## Customer Journey Optimization

### Personalized Email Campaigns

**Workflow**:
1. Customer data is segmented based on behavior
2. Claude generates personalized email content for each segment
3. A/B testing variants are created
4. Emails are scheduled and performance is tracked

**Example Template**:
```
Create a personalized email for a customer with the following attributes:
- Purchase history: {{$json.purchaseHistory}}
- Browsing behavior: {{$json.browsingBehavior}}
- Previous interactions: {{$json.previousInteractions}}
- Segment: {{$json.customerSegment}}

The email should:
1. Reference their specific interests or purchases
2. Include a personalized recommendation
3. Have a compelling subject line
4. Include a clear call-to-action
```

### Customer Churn Prediction and Prevention

**Workflow**:
1. Customer activity data is analyzed for churn indicators
2. At-risk customers are identified
3. Claude generates personalized retention messages
4. Customer success teams receive prioritized outreach lists

**Benefits**:
- Proactively addresses customer satisfaction issues
- Personalizes retention strategies
- Improves overall customer retention

## Implementing These Use Cases

Each of these use cases can be implemented using the workflow templates in this repository as a starting point. By combining Claude's intelligence with n8n's automation capabilities, you can build powerful solutions that save time, improve quality, and deliver better experiences.

For implementation assistance or custom use case development, refer to the n8n and Anthropic documentation or reach out to their respective support channels.
