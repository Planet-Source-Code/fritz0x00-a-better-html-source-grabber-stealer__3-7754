<div align="center">

## ^\!\!\~ A better HTML Source Grabber/Stealer \~\!\!^


</div>

### Description

Simple example of how to grab(some people like ti call it 'steal') the HTML source of a page from a application... There are a couple of examples here at PSC, but they are not very good because they use ReadHuge to store all of the data in a buffer which can cause memory problems, incomplete page sources, and of course ugly boxes due to no carriage returns or line breaks... This ReadString version is alot more efficent... It works 100% in MFC... And since this code is so easy to implement into virtually any project, I am NOT going to post the project files unless I get alot of requests
 
### More Info
 
Make sure to define m_strURL and m_strSource via ClassWizard


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[fritz0x00](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/fritz0x00.md)
**Level**          |Advanced
**User Rating**    |5.0 (20 globes from 4 users)
**Compatibility**  |C\+\+ \(general\), Microsoft Visual C\+\+
**Category**       |[Internet/ Browsers/ HTML](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/internet-browsers-html__3-9.md)
**World**          |[C / C\+\+](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/c-c.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/fritz0x00-a-better-html-source-grabber-stealer__3-7754/archive/master.zip)

### API Declarations

```
#include <afxinet.h>
```


### Source Code

```
//** Make sure you add two edit boxes to your dialog, make the one for the URL input a CString named 'm_strURL'
//** And to store the source add another edit box(Make sure its multi line), make it a CString named 'm_strSource'
void CYourDialogClass::OnYourEvent()
{
	UpdateData(TRUE); //** Perform DDX and get user input
	CInternetSession session; //** define our internet session
	CInternetFile* pFile = (CInternetFile *)session.OpenURL(m_strURL); //** define our internet file that will hold the source
	if(pFile) //** If we can OpenURL(m_strURL)
	{
		CString string; //** Create a buffer string
		while (pFile->ReadString(string) != NULL) //** Read as many string as we can until we run into EOF(End Of File)
		{
			m_strSource += string; //** Add the string of data we just read
			m_strSource += "\r\n"; //** Add a line break to make it look better
		}
	}
	UpdateData(FALSE);
}
```

