# CrewAI Customer Support Automation

An intelligent multi-agent customer support system built with CrewAI that provides automated, high-quality customer service through specialized AI agents working in collaboration.

## Repository Name
`crewai-customer-support`

## Overview

This project demonstrates how to create an automated customer support system using AI agents that embody the six key elements of effective agent performance:

- **Role Playing**: Agents assume specific professional roles
- **Focus**: Clear goals and specialized responsibilities
- **Tools**: Access to documentation and web scraping capabilities
- **Cooperation**: Agents can delegate and collaborate
- **Guardrails**: Built-in quality controls and professional standards
- **Memory**: Persistent context across interactions

## Features

- **Dual-Agent System**: Support representative and quality assurance specialist
- **Intelligent Tool Usage**: Automated documentation scraping and research
- **Quality Assurance**: Built-in review and improvement process
- **Memory Persistence**: Context retention across customer interactions
- **Professional Standards**: Guardrails ensure appropriate responses
- **Flexible Input**: Customizable customer inquiries and scenarios

## Installation

1. Clone this repository:
```bash
git clone https://github.com/yourusername/crewai-customer-support.git
cd crewai-customer-support
```

2. Install the required dependencies:
```bash
pip install -r requirements.txt
```

3. Set up your OpenAI API key:
```bash
export OPENAI_API_KEY="your-api-key-here"
```

## Dependencies

```
crewai==0.28.8
crewai_tools==0.1.6
langchain_community==0.0.29
```

## Usage

### Basic Customer Support Flow

```python
from crewai import Agent, Task, Crew
from crewai_tools import ScrapeWebsiteTool

# Initialize the customer support crew
crew = Crew(
    agents=[support_agent, support_quality_assurance_agent],
    tasks=[inquiry_resolution, quality_assurance_review],
    verbose=2,
    memory=True
)

# Process a customer inquiry
inputs = {
    "customer": "Your Company Name",
    "person": "Customer Name",
    "inquiry": "Customer's question or issue"
}

result = crew.kickoff(inputs=inputs)
```

### Example Customer Inquiry

```python
inputs = {
    "customer": "TechCorp",
    "person": "Sarah Johnson",
    "inquiry": "I need help setting up a Crew and adding memory to it. Can you provide guidance?"
}

result = crew.kickoff(inputs=inputs)
print(result)
```

## Agent Roles

### Senior Support Representative
- **Role**: Primary customer support specialist
- **Goal**: Provide the most friendly and helpful support possible
- **Capabilities**: 
  - Access to documentation scraping tools
  - Direct customer interaction
  - Complete and accurate response generation
- **Delegation**: Cannot delegate (focused on direct support)

### Support Quality Assurance Specialist
- **Role**: Quality control and review specialist  
- **Goal**: Ensure highest quality support standards
- **Capabilities**:
  - Review and improve support responses
  - Ensure comprehensive coverage of customer inquiries
  - Maintain professional and friendly tone
- **Delegation**: Can delegate back to support representative

## Workflow

1. **Inquiry Processing**: Support agent receives and analyzes customer inquiry
2. **Research & Response**: Agent uses available tools to gather information and craft response
3. **Quality Review**: QA specialist reviews the response for completeness and quality
4. **Final Output**: Polished, professional response ready for customer delivery

## Available Tools

### Documentation Scraping
- **ScrapeWebsiteTool**: Automatically scrapes relevant documentation
- **SerperDevTool**: Web search capabilities (configurable)
- **WebsiteSearchTool**: Targeted website search (configurable)

### Custom Tool Integration
The system supports integration of custom tools for:
- Customer data loading
- Previous conversation history
- CRM integration
- Bug report checking
- Feature request tracking
- Ticket management

## Configuration

### Memory Settings
```python
crew = Crew(
    agents=[support_agent, qa_agent],
    tasks=[inquiry_task, review_task],
    verbose=2,
    memory=True  # Enables persistent memory
)
```

### Tool Assignment
Tools can be assigned at two levels:

**Agent Level** (available for all tasks):
```python
agent = Agent(
    role="Support Agent",
    tools=[scrape_tool, search_tool]
)
```

**Task Level** (specific to individual tasks):
```python
task = Task(
    description="Handle customer inquiry",
    tools=[docs_scrape_tool],
    agent=support_agent
)
```

## Customization

### Adding Custom Tools
```python
from crewai_tools import BaseTool

class CustomCRMTool(BaseTool):
    name: str = "CRM Lookup"
    description: str = "Look up customer information in CRM"
    
    def _run(self, customer_id: str) -> str:
        # Your CRM integration logic
        return customer_data
```

### Modifying Agent Behavior
Agents can be customized with:
- Different backstories and personalities
- Specialized knowledge domains
- Custom response templates
- Industry-specific terminology

## Output Format

The system generates professional customer support responses with:
- Comprehensive coverage of customer questions
- Friendly and helpful tone
- Reference citations for information sources
- Clear, actionable guidance
- Professional formatting

## Example Response Structure

```markdown
Hi [Customer Name],

Thank you for reaching out about [topic]. I'd be happy to help you with [specific issue].

[Detailed explanation with step-by-step guidance]

[Additional resources or references]

Please let me know if you have any other questions!

Best regards,
Support Team
```

## Memory and Context

The system maintains memory across interactions, enabling:
- Context-aware responses
- Reference to previous conversations
- Cumulative knowledge building
- Personalized support experience

## Quality Assurance Features

- **Completeness Check**: Ensures all aspects of inquiry are addressed
- **Tone Verification**: Maintains friendly, professional communication
- **Accuracy Review**: Validates information and sources
- **Standard Compliance**: Adheres to company support guidelines

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/support-enhancement`)
3. Commit your changes (`git commit -m 'Add support enhancement'`)
4. Push to the branch (`git push origin feature/support-enhancement`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- Built with [CrewAI](https://crewai.com/) framework
- Powered by OpenAI's language models
- Demonstrates advanced multi-agent customer support automation

## Support

If you encounter any issues or have questions about implementing this customer support system, please open an issue in the GitHub repository.

---

**Note**: This system demonstrates automated customer support capabilities. Always review and customize responses according to your company's specific policies and requirements.
