1. LanguageTool
We can use LanguageTool in python using the library language-tool-python. It is an open source tool to check grammar and spelling mistakes which means it is available for free without any registration.

To install the python library for LanguageTool, run the command below.

pip install language-tool-python
Let's take a sample text to explain this library with an example.

Sample Text : I is testng grammar tool using python. It does not costt anythng.
Code
In the program below, we are loading the library first and then running the library on input text. It returns the corrected text after fixing spelling mistakes and grammar.

import language_tool_python

mytext = """
I is testng grammar tool using python. It does not costt anythng.
"""

def grammarCorrector(text):
    tool = language_tool_python.LanguageTool('en-US')
    result = tool.correct(text)
    return result

output_data = grammarCorrector(mytext)
print(output_data)
Output
I am testing grammar tool using python. It does not cost anything.
How to Check Grammar
In the previous section, it automatically corrects grammar in the sentence. Here we are interested to see the grammar and spelling mistakes in the text along with the replacements suggested by the tool.

def grammarChecker(text):
    tool = language_tool_python.LanguageTool('en-US')
    result = tool.check(text)
    return result

output_data = grammarChecker(mytext)
print(output_data)
Output

[Match({'ruleId': 'PERS_PRONOUN_AGREEMENT', 'message': 'Did you mean “am” or “will be”?', 'replacements': ['am', 'will be'], 'offsetInContext': 3, 'context': ' I is testng grammar tool using python. It do...', 'offset': 3, 'errorLength': 2, 'category': 'GRAMMAR', 'ruleIssueType': 'grammar', 'sentence': 'I is testng grammar tool using python.'}), Match({'ruleId': 'MORFOLOGIK_RULE_EN_US', 'message': 'Possible spelling mistake found.', 'replacements': ['testing'], 'offsetInContext': 6, 'context': ' I is testng grammar tool using python. It does not ...', 'offset': 6, 'errorLength': 6, 'category': 'TYPOS', 'ruleIssueType': 'misspelling', 'sentence': 'I is testng grammar tool using python.'}), Match({'ruleId': 'MORFOLOGIK_RULE_EN_US', 'message': 'Possible spelling mistake found.', 'replacements': ['cost', 'costs', 'Costa'], 'offsetInContext': 43, 'context': '... grammar tool using python. It does not costt anythng. ', 'offset': 52, 'errorLength': 5, 'category': 'TYPOS', 'ruleIssueType': 'misspelling', 'sentence': 'It does not costt anythng.'}), Match({'ruleId': 'MORFOLOGIK_RULE_EN_US', 'message': 'Possible spelling mistake found.', 'replacements': ['anything'], 'offsetInContext': 43, 'context': '...ar tool using python. It does not costt anythng. ', 'offset': 58, 'errorLength': 7, 'category': 'TYPOS', 'ruleIssueType': 'misspelling', 'sentence': 'It does not costt anythng.'})]
To see the number of errors, use the code below.

len(output_data)
# 4
To see the detailed description of the first issue in the text, use the command below.

output_data[0]
Match({'ruleId': 'PERS_PRONOUN_AGREEMENT', 'message': 'Did you mean “am” or “will be”?', 'replacements': ['am', 'will be'], 'offsetInContext': 3, 'context': ' I is testng grammar tool using python. It do...', 'offset': 3, 'errorLength': 2, 'category': 'GRAMMAR', 'ruleIssueType': 'grammar', 'sentence': 'I is testng grammar tool using python.'})
To see the replacements suggested by the tool for the first issue, use the command below.

output_data[0].replacements
# ['am', 'will be']
