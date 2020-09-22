<div align="center">

## Grab the current URL from IE


</div>

### Description

This code will show you how to find the Internet Explorer browser window, then grab the current URL out of the IE address bar. Perfect for learning simple win32 api functions in delphi.
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Bryan Hammond](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/bryan-hammond.md)
**Level**          |Intermediate
**User Rating**    |4.8 (24 globes from 5 users)
**Compatibility**  |Delphi 5, Delphi 4
**Category**       |[Windows API Call/ Explanation](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/windows-api-call-explanation__7-39.md)
**World**          |[Delphi](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/delphi.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/bryan-hammond-grab-the-current-url-from-ie__7-211/archive/master.zip)





### Source Code

```
<pre><i><span style='color:green'>{-------------------------------------------------------}</span></i><o:p></o:p></pre><pre><b><span
style='color:red'>Function</span></b> GetText<b><span style='font-size:12.0pt;
color:blue'>(</span></b>WindowHandle<b><span style='font-size:12.0pt;
color:blue'>:</span></b> hwnd<b><span style='font-size:12.0pt;color:blue'>):</span><span
style='color:red'>string</span></b><b><span style='font-size:12.0pt;color:blue'>;</span></b><o:p></o:p></pre><pre><b><span
style='color:red'>var</span></b><o:p></o:p></pre><pre>txtLength <b><span
style='font-size:12.0pt;color:blue'>:</span></b> integer<b><span
style='font-size:12.0pt;color:blue'>;</span></b><o:p></o:p></pre><pre>buffer<b><span
style='font-size:12.0pt;color:blue'>:</span></b> <b><span style='color:red'>string</span></b><b><span
style='font-size:12.0pt;color:blue'>;</span></b><o:p></o:p></pre><pre><b><span
style='color:red'>begin</span></b><o:p></o:p></pre><pre> TxtLength <b><span
style='font-size:12.0pt;color:blue'>:</span></b><span style='font-size:12.0pt;
color:blue'>=</span> SendMessage<b><span style='font-size:12.0pt;color:blue'>(</span></b>WindowHandle<b><span
style='font-size:12.0pt;color:blue'>,</span></b> WM_GETTEXTLENGTH<b><span
style='font-size:12.0pt;color:blue'>,</span></b> <span style='color:brown'>0</span><b><span
style='font-size:12.0pt;color:blue'>,</span></b> <span style='color:brown'>0</span><b><span
style='font-size:12.0pt;color:blue'>);</span></b><o:p></o:p></pre><pre> txtlength <b><span
style='font-size:12.0pt;color:blue'>:</span></b><span style='font-size:12.0pt;
color:blue'>=</span> txtlength <span style='font-size:12.0pt;color:blue'>+</span> <span
style='color:brown'>1</span><b><span style='font-size:12.0pt;color:blue'>;</span></b><o:p></o:p></pre><pre> setlength <b><span
style='font-size:12.0pt;color:blue'>(</span></b>buffer<b><span
style='font-size:12.0pt;color:blue'>,</span></b> txtlength<b><span
style='font-size:12.0pt;color:blue'>);</span></b><o:p></o:p></pre><pre> sendmessage <b><span
style='font-size:12.0pt;color:blue'>(</span></b>WindowHandle<b><span
style='font-size:12.0pt;color:blue'>,</span></b>wm_gettext<b><span
style='font-size:12.0pt;color:blue'>,</span></b> txtlength<b><span
style='font-size:12.0pt;color:blue'>,</span></b> longint<b><span
style='font-size:12.0pt;color:blue'>(</span></b><span style='font-size:12.0pt;
color:blue'>@</span>buffer<b><span style='font-size:12.0pt;color:blue'>[</span></b><span
style='color:brown'>1</span><b><span style='font-size:12.0pt;color:blue'>]));</span></b><o:p></o:p></pre><pre> result <b><span
style='font-size:12.0pt;color:blue'>:</span></b><span style='font-size:12.0pt;
color:blue'>=</span> buffer<b><span style='font-size:12.0pt;color:blue'>;</span></b><o:p></o:p></pre><pre><b><span
style='color:red'>end</span></b><b><span style='font-size:12.0pt;color:blue'>;</span></b><o:p></o:p></pre><pre><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></pre><pre><b><span
style='color:red'>function</span></b> GetURL<b><span style='font-size:12.0pt;
color:blue'>:</span><span style='color:red'>string</span></b><b><span
style='font-size:12.0pt;color:blue'>;</span></b><o:p></o:p></pre><pre><b><span
style='color:red'>var</span></b><o:p></o:p></pre><pre>ie<b><span
style='font-size:12.0pt;color:blue'>,</span></b>toolbar<b><span
style='font-size:12.0pt;color:blue'>,</span></b>combo<b><span style='font-size:
12.0pt;color:blue'>,</span></b><o:p></o:p></pre><pre>comboboxex<b><span
style='font-size:12.0pt;color:blue'>,</span></b>edit<b><span style='font-size:
12.0pt;color:blue'>,</span></b><o:p></o:p></pre><pre>worker<b><span
style='font-size:12.0pt;color:blue'>,</span></b>toolbarwindow<b><span
style='font-size:12.0pt;color:blue'>:</span></b>hwnd<b><span style='font-size:
12.0pt;color:blue'>;</span></b><o:p></o:p></pre><pre><b><span style='color:
red'>begin</span></b><o:p></o:p></pre><pre><span style="mso-spacerun: yes">  </span>ie <b><span
style='font-size:12.0pt;color:blue'>:</span></b><span style='font-size:12.0pt;
color:blue'>=</span> FindWindow<b><span style='font-size:12.0pt;color:blue'>(</span></b>pchar<b><span
style='font-size:12.0pt;color:blue'>(</span></b><span style='color:purple'>'IEFrame'</span><b><span
style='font-size:12.0pt;color:blue'>),</span><span style='color:red'>nil</span></b><b><span
style='font-size:12.0pt;color:blue'>);</span></b><o:p></o:p></pre><pre><span style="mso-spacerun: yes">  </span>worker <b><span
style='font-size:12.0pt;color:blue'>:</span></b><span style='font-size:12.0pt;
color:blue'>=</span> FindWindowEx<b><span style='font-size:12.0pt;color:blue'>(</span></b>ie<b><span
style='font-size:12.0pt;color:blue'>,</span></b><span style='color:brown'>0</span><b><span
style='font-size:12.0pt;color:blue'>,</span></b><span style='color:purple'>'WorkerA'</span><b><span
style='font-size:12.0pt;color:blue'>,</span><span style='color:red'>nil</span></b><b><span
style='font-size:12.0pt;color:blue'>);</span></b><o:p></o:p></pre><pre><span style="mso-spacerun: yes">  </span>toolbar <b><span
style='font-size:12.0pt;color:blue'>:</span></b><span style='font-size:12.0pt;
color:blue'>=</span> FindWindowEx<b><span style='font-size:12.0pt;color:blue'>(</span></b>worker<b><span
style='font-size:12.0pt;color:blue'>,</span></b><span style='color:brown'>0</span><b><span
style='font-size:12.0pt;color:blue'>,</span></b><span style='color:purple'>'rebarwindow32'</span><b><span
style='font-size:12.0pt;color:blue'>,</span><span style='color:red'>nil</span></b><b><span
style='font-size:12.0pt;color:blue'>);</span></b><o:p></o:p></pre><pre><span style="mso-spacerun: yes">  </span>comboboxex <b><span
style='font-size:12.0pt;color:blue'>:</span></b><span style='font-size:12.0pt;
color:blue'>=</span> FindWindowEx<b><span style='font-size:12.0pt;color:blue'>(</span></b>toolbar<b><span
style='font-size:12.0pt;color:blue'>,</span></b> <span style='color:brown'>0</span><b><span
style='font-size:12.0pt;color:blue'>,</span></b> <span style='color:purple'>'comboboxex32'</span><b><span
style='font-size:12.0pt;color:blue'>,</span></b> <b><span style='color:red'>nil</span></b><b><span
style='font-size:12.0pt;color:blue'>);</span></b><o:p></o:p></pre><pre><span style="mso-spacerun: yes">  </span>combo <b><span
style='font-size:12.0pt;color:blue'>:</span></b><span style='font-size:12.0pt;
color:blue'>=</span> FindWindowEx<b><span style='font-size:12.0pt;color:blue'>(</span></b>comboboxex<b><span
style='font-size:12.0pt;color:blue'>,</span></b><span style='color:brown'>0</span><b><span
style='font-size:12.0pt;color:blue'>,</span></b><span style='color:purple'>'ComboBox'</span><b><span
style='font-size:12.0pt;color:blue'>,</span><span style='color:red'>nil</span></b><b><span
style='font-size:12.0pt;color:blue'>);</span></b><o:p></o:p></pre><pre><span style="mso-spacerun: yes">  </span>edit <b><span
style='font-size:12.0pt;color:blue'>:</span></b><span style='font-size:12.0pt;
color:blue'>=</span> FindWindowEx<b><span style='font-size:12.0pt;color:blue'>(</span></b>combo<b><span
style='font-size:12.0pt;color:blue'>,</span></b><span style='color:brown'>0</span><b><span
style='font-size:12.0pt;color:blue'>,</span></b><span style='color:purple'>'Edit'</span><b><span
style='font-size:12.0pt;color:blue'>,</span><span style='color:red'>nil</span></b><b><span
style='font-size:12.0pt;color:blue'>);</span></b><o:p></o:p></pre><pre><span style="mso-spacerun: yes">  </span>toolbarwindow <b><span
style='font-size:12.0pt;color:blue'>:</span></b><span style='font-size:12.0pt;
color:blue'>=</span> FindWindowEx<b><span style='font-size:12.0pt;color:blue'>(</span></b>comboboxex<b><span
style='font-size:12.0pt;color:blue'>,</span></b> <span style='color:brown'>0</span><b><span
style='font-size:12.0pt;color:blue'>,</span></b> <span style='color:purple'>'toolbarwindow32'</span><b><span
style='font-size:12.0pt;color:blue'>,</span></b> <b><span style='color:red'>nil</span></b><b><span
style='font-size:12.0pt;color:blue'>);</span></b><o:p></o:p></pre><pre><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></pre><pre><span style="mso-spacerun: yes">  </span>result <b><span
style='font-size:12.0pt;color:blue'>:</span></b><span style='font-size:12.0pt;
color:blue'>=</span> GetText<b><span style='font-size:12.0pt;color:blue'>(</span></b>edit<b><span
style='font-size:12.0pt;color:blue'>);</span></b><o:p></o:p></pre><pre><i><span
style='color:green'>{-------------------------------------------------------}</span></i><o:p></o:p></pre><pre><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></pre><pre><b><span
style='color:red'>procedure</span></b> TForm1<b><span style='font-size:13.5pt;
color:blue'>.</span></b>Button1Click<b><span style='font-size:12.0pt;
color:blue'>(</span></b>Sender<b><span style='font-size:12.0pt;color:blue'>:</span></b> TObject<b><span
style='font-size:12.0pt;color:blue'>);</span></b><o:p></o:p></pre><pre><b><span
style='color:red'>begin</span></b><o:p></o:p></pre><pre>showmessage<b><span
style='font-size:12.0pt;color:blue'>(</span></b>GetURL<b><span
style='font-size:12.0pt;color:blue'>);</span></b><o:p></o:p></pre><pre><b><span
style='color:red'>end</span></b><b><span style='font-size:12.0pt;color:blue'>;</span></b><o:p></o:p></pre>
```

