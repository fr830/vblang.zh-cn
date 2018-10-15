# <a name="documentation-comments"></a><span data-ttu-id="121f9-101">文档注释</span><span class="sxs-lookup"><span data-stu-id="121f9-101">Documentation Comments</span></span>

<span data-ttu-id="121f9-102">文档注释是特殊格式进行分析以生成有关其附加到的代码文档的源中的注释。</span><span class="sxs-lookup"><span data-stu-id="121f9-102">Documentation comments are specially formatted comments in the source that can be analyzed to produce documentation about the code they are attached to.</span></span> <span data-ttu-id="121f9-103">文档注释的基本格式为 XML。</span><span class="sxs-lookup"><span data-stu-id="121f9-103">The basic format for documentation comments is XML.</span></span> <span data-ttu-id="121f9-104">当包含文档注释的编译代码，编译器可能会选择性地将发出一个 XML 文件，代表源中的文档注释的总和。</span><span class="sxs-lookup"><span data-stu-id="121f9-104">When the compiling code with documentation comments, the compiler may optionally emit an XML file that represents the sum total of the documentation comments in the source.</span></span> <span data-ttu-id="121f9-105">此 XML 文件然后可由其他工具来生成印刷品或联机文档。</span><span class="sxs-lookup"><span data-stu-id="121f9-105">This XML file can then be used by other tools to produce printed or online documentation.</span></span>

<span data-ttu-id="121f9-106">本章介绍了文档注释，建议用于文档注释的 XML 标记。</span><span class="sxs-lookup"><span data-stu-id="121f9-106">This chapter describes document comments and recommended XML tags to use with document comments.</span></span>

## <a name="documentation-comment-format"></a><span data-ttu-id="121f9-107">文档注释格式</span><span class="sxs-lookup"><span data-stu-id="121f9-107">Documentation Comment Format</span></span>

<span data-ttu-id="121f9-108">文档注释是开头的特殊注释`'''`，三个单引号标记。</span><span class="sxs-lookup"><span data-stu-id="121f9-108">Document comments are special comments that begin with `'''`, three single quote marks.</span></span> <span data-ttu-id="121f9-109">它们必须紧跟在记录的类型 （如类、 委托或接口） 或类型成员 （例如字段、 事件、 属性或方法）。</span><span class="sxs-lookup"><span data-stu-id="121f9-109">They must immediately precede the type (such as a class, delegate, or interface) or type member (such as a field, event, property, or method) that they document.</span></span> <span data-ttu-id="121f9-110">如果有的话，在提供其主体中，该方法的文档注释将被替换分部方法声明上的文档注释。</span><span class="sxs-lookup"><span data-stu-id="121f9-110">A document comment on a partial method declaration will be replaced by the document comment on the method that supplies its body, if there is one.</span></span> <span data-ttu-id="121f9-111">一起追加所有相邻的文档注释，以生成单个文档注释。</span><span class="sxs-lookup"><span data-stu-id="121f9-111">All adjacent document comments are appended together to produce a single document comment.</span></span> <span data-ttu-id="121f9-112">如果没有空格字符以下`'''`字符，则该空白字符不包括在串联。</span><span class="sxs-lookup"><span data-stu-id="121f9-112">If there is a whitespace character following the `'''` characters, then that whitespace character is not included in the concatenation.</span></span> <span data-ttu-id="121f9-113">例如：</span><span class="sxs-lookup"><span data-stu-id="121f9-113">For example:</span></span>

```vb
''' <remarks>
''' Class <c>Point</c> models a point in a two-dimensional plane.
''' </remarks>
Public Class Point 
   ''' <remarks>
   ''' Method <c>Draw</c> renders the point.
   ''' </remarks>
   Sub Draw()
   End Sub
End Class
```

<span data-ttu-id="121f9-114">文档注释必须格式正确的 XML 符合以下 http://www.w3.org/TR/REC-xml。</span><span class="sxs-lookup"><span data-stu-id="121f9-114">Documentation comments must be well formed XML according to http://www.w3.org/TR/REC-xml.</span></span> <span data-ttu-id="121f9-115">如果 XML 的格式不正确，则会生成警告，并且文档文件将包含条注释，指出遇到错误。</span><span class="sxs-lookup"><span data-stu-id="121f9-115">If the XML is not well formed, a warning is generated and the documentation file will contain a comment saying that an error was encountered.</span></span>

<span data-ttu-id="121f9-116">尽管开发人员可以随意创建其自己的标记集下, 一节中定义一组推荐。</span><span class="sxs-lookup"><span data-stu-id="121f9-116">Although developers are free to create their own set of tags, a recommended set is defined in the next section.</span></span> <span data-ttu-id="121f9-117">部分建议标记具有特殊含义：</span><span class="sxs-lookup"><span data-stu-id="121f9-117">Some of the recommended tags have special meanings:</span></span>

* <span data-ttu-id="121f9-118">`<param>`标记用于描述参数。</span><span class="sxs-lookup"><span data-stu-id="121f9-118">The `<param>` tag is used to describe parameters.</span></span> <span data-ttu-id="121f9-119">指定的参数`<param>`标记必须存在和类型成员的所有参数必须文档注释中所都述。</span><span class="sxs-lookup"><span data-stu-id="121f9-119">The parameter specified by a `<param>` tag must exist and all parameters of the type member must be described in the documentation comment.</span></span> <span data-ttu-id="121f9-120">如果任何一个条件未得到满足，编译器会发出警告。</span><span class="sxs-lookup"><span data-stu-id="121f9-120">If either condition is not true, the compiler issues a warning.</span></span>

* <span data-ttu-id="121f9-121">`cref` 属性可以附加到任何标记，以提供对代码元素的引用。</span><span class="sxs-lookup"><span data-stu-id="121f9-121">The `cref` attribute can be attached to any tag to provide a reference to a code element.</span></span> <span data-ttu-id="121f9-122">代码元素必须存在;在编译时编译器将名称替换为表示该成员的 ID 字符串。</span><span class="sxs-lookup"><span data-stu-id="121f9-122">The code element must exist; at compile-time the compiler replaces the name with the ID string representing the member.</span></span> <span data-ttu-id="121f9-123">如果代码元素不存在，编译器会发出警告。</span><span class="sxs-lookup"><span data-stu-id="121f9-123">If the code element does not exist, the compiler issues a warning.</span></span> <span data-ttu-id="121f9-124">当查找名称中所述`cref`特性，编译器仍会遵循`Imports`出现在包含源文件的语句。</span><span class="sxs-lookup"><span data-stu-id="121f9-124">When looking for a name described in a `cref` attribute, the compiler respects `Imports` statements that appear within the containing source file.</span></span>

* <span data-ttu-id="121f9-125">`<summary>`标记应使用文档查看器以显示有关类型或成员的其他信息。</span><span class="sxs-lookup"><span data-stu-id="121f9-125">The `<summary>` tag is intended to be used by a documentation viewer to display additional information about a type or member.</span></span>

<span data-ttu-id="121f9-126">请注意，文档文件不提供文档注释中包含的内容仅相关类型和成员的完整信息。</span><span class="sxs-lookup"><span data-stu-id="121f9-126">Note that the documentation file does not provide full information about a type and members, only what is contained in the document comments.</span></span> <span data-ttu-id="121f9-127">若要获取有关类型或成员的详细信息，必须与实际类型或成员上反射结合使用的文档文件。</span><span class="sxs-lookup"><span data-stu-id="121f9-127">To get more information about a type or member, the documentation file must be used in conjunction with reflection on the actual type or member.</span></span>

## <a name="recommended-tags"></a><span data-ttu-id="121f9-128">建议的标记</span><span class="sxs-lookup"><span data-stu-id="121f9-128">Recommended tags</span></span>

<span data-ttu-id="121f9-129">文档生成器必须接受并处理根据 XML 的规则是有效的任何标记。</span><span class="sxs-lookup"><span data-stu-id="121f9-129">The documentation generator must accept and process any tag that is valid according to the rules of XML.</span></span> <span data-ttu-id="121f9-130">下列标记提供用户文档中的常用功能：</span><span class="sxs-lookup"><span data-stu-id="121f9-130">The following tags provide commonly used functionality in user documentation:</span></span>

<span data-ttu-id="121f9-131">`<c>` 设置类似于代码的字体中的文本</span><span class="sxs-lookup"><span data-stu-id="121f9-131">`<c>` Sets text in a code-like font</span></span>

<span data-ttu-id="121f9-132">`<code>` 类似于代码的字体中设置源的代码或程序输出的一个或多个的行</span><span class="sxs-lookup"><span data-stu-id="121f9-132">`<code>` Sets one or more lines of source code or program output in a code-like font</span></span>

<span data-ttu-id="121f9-133">`<example>` 指示一个示例</span><span class="sxs-lookup"><span data-stu-id="121f9-133">`<example>` Indicates an example</span></span>

<span data-ttu-id="121f9-134">`<exception>` 标识一个方法可能会引发的异常</span><span class="sxs-lookup"><span data-stu-id="121f9-134">`<exception>` Identifies the exceptions a method can throw</span></span>

<span data-ttu-id="121f9-135">`<include>` 包括外部 XML 文档</span><span class="sxs-lookup"><span data-stu-id="121f9-135">`<include>` Includes an external XML document</span></span>

<span data-ttu-id="121f9-136">`<list>` 创建列表或表</span><span class="sxs-lookup"><span data-stu-id="121f9-136">`<list>` Creates a list or table</span></span>

<span data-ttu-id="121f9-137">`<para>` 允许结构添加到文本</span><span class="sxs-lookup"><span data-stu-id="121f9-137">`<para>` Permits structure to be added to text</span></span>

<span data-ttu-id="121f9-138">`<param>` 描述的方法或构造函数的参数</span><span class="sxs-lookup"><span data-stu-id="121f9-138">`<param>` Describes a parameter for a method or constructor</span></span>

<span data-ttu-id="121f9-139">`<paramref>` 标识一个字为参数名称</span><span class="sxs-lookup"><span data-stu-id="121f9-139">`<paramref>` Identifies that a word is a parameter name</span></span>

<span data-ttu-id="121f9-140">`<permission>` 记录成员的安全可访问性</span><span class="sxs-lookup"><span data-stu-id="121f9-140">`<permission>` Documents the security accessibility of a member</span></span>

<span data-ttu-id="121f9-141">`<remarks>` 介绍一种类型</span><span class="sxs-lookup"><span data-stu-id="121f9-141">`<remarks>` Describes a type</span></span>

<span data-ttu-id="121f9-142">`<returns>` 描述一种方法的返回值</span><span class="sxs-lookup"><span data-stu-id="121f9-142">`<returns>` Describes the return value of a method</span></span>

<span data-ttu-id="121f9-143">`<see>` 指定的链接</span><span class="sxs-lookup"><span data-stu-id="121f9-143">`<see>` Specifies a link</span></span>

<span data-ttu-id="121f9-144">`<seealso>` 生成的另请参阅条目</span><span class="sxs-lookup"><span data-stu-id="121f9-144">`<seealso>` Generates a See Also entry</span></span>

<span data-ttu-id="121f9-145">`<summary>` 描述一种类型的成员</span><span class="sxs-lookup"><span data-stu-id="121f9-145">`<summary>` Describes a member of a type</span></span>

<span data-ttu-id="121f9-146">`<typeparam>` 描述类型参数</span><span class="sxs-lookup"><span data-stu-id="121f9-146">`<typeparam>` Describes a type parameter</span></span>

<span data-ttu-id="121f9-147">`<value>` 描述的属性</span><span class="sxs-lookup"><span data-stu-id="121f9-147">`<value>` Describes a property</span></span>

### <a name="ltcgt"></a><span data-ttu-id="121f9-148">&lt;c&gt;</span><span class="sxs-lookup"><span data-stu-id="121f9-148">&lt;c&gt;</span></span>

<span data-ttu-id="121f9-149">此标记指定的片段说明中的文本应使用类似的代码块使用的字体。</span><span class="sxs-lookup"><span data-stu-id="121f9-149">This tag specifies that a fragment of text within a description should use a font like that used for a block of code.</span></span> <span data-ttu-id="121f9-150">(对于实际代码行，请使用`<code>`。)</span><span class="sxs-lookup"><span data-stu-id="121f9-150">(For lines of actual code, use `<code>`.)</span></span>

<span data-ttu-id="121f9-151">__语法：__</span><span class="sxs-lookup"><span data-stu-id="121f9-151">__Syntax:__</span></span>

```xml
<c>text to be set like code</c>
```

<span data-ttu-id="121f9-152">__示例：__</span><span class="sxs-lookup"><span data-stu-id="121f9-152">__Example:__</span></span>

```vb
''' <remarks>
''' Class <c>Point</c> models a point in a two-dimensional plane.
''' </remarks>
Public Class Point 
End Class
```

### <a name="ltcodegt"></a><span data-ttu-id="121f9-153">&lt;代码&gt;</span><span class="sxs-lookup"><span data-stu-id="121f9-153">&lt;code&gt;</span></span>

<span data-ttu-id="121f9-154">此标记指定一个或多个源的代码或程序输出行应使用固定宽度字体。</span><span class="sxs-lookup"><span data-stu-id="121f9-154">This tag specifies that one or more lines of source code or program output should use a fixed-width font.</span></span> <span data-ttu-id="121f9-155">(对于小型代码片段使用`<c>`。)</span><span class="sxs-lookup"><span data-stu-id="121f9-155">(For small code fragments, use `<c>`.)</span></span>

<span data-ttu-id="121f9-156">__语法：__</span><span class="sxs-lookup"><span data-stu-id="121f9-156">__Syntax:__</span></span>

```xml
<code>source code or program output</code>
```

<span data-ttu-id="121f9-157">__示例：__</span><span class="sxs-lookup"><span data-stu-id="121f9-157">__Example:__</span></span>

```vb
''' <summary>
''' This method changes the point's location by the given x- and 
''' y-offsets.
''' <example>
''' For example:
''' <code>
'''    Dim p As Point = New Point(3,5)
'''    p.Translate(-1,3)
''' </code>
''' results in <c>p</c>'s having the value (2,8).
''' </example>
''' </summary>
Public Sub Translate(x As Integer, y As Integer)
    Me.x += x
    Me.y += y
End Sub
```

### <a name="ltexamplegt"></a><span data-ttu-id="121f9-158">&lt;example&gt;</span><span class="sxs-lookup"><span data-stu-id="121f9-158">&lt;example&gt;</span></span>

<span data-ttu-id="121f9-159">此标记允许的代码示例显示如何使用元素的注释内。</span><span class="sxs-lookup"><span data-stu-id="121f9-159">This tag allows example code within a comment to show how an element can be used.</span></span> <span data-ttu-id="121f9-160">通常，这将涉及到使用标记的`<code>`也。</span><span class="sxs-lookup"><span data-stu-id="121f9-160">Ordinarily, this will involve use of the tag `<code>` as well.</span></span>

<span data-ttu-id="121f9-161">__语法：__</span><span class="sxs-lookup"><span data-stu-id="121f9-161">__Syntax:__</span></span>

```xml
<example>description</example>
```

<span data-ttu-id="121f9-162">__示例：__</span><span class="sxs-lookup"><span data-stu-id="121f9-162">__Example:__</span></span>

<span data-ttu-id="121f9-163">有关示例，请参见 `<code>`。</span><span class="sxs-lookup"><span data-stu-id="121f9-163">See `<code>` for an example.</span></span>

### <a name="ltexceptiongt"></a><span data-ttu-id="121f9-164">&lt;exception&gt;</span><span class="sxs-lookup"><span data-stu-id="121f9-164">&lt;exception&gt;</span></span>

<span data-ttu-id="121f9-165">此标记提供了一种方法来记录的方法可能引发的异常。</span><span class="sxs-lookup"><span data-stu-id="121f9-165">This tag provides a way to document the exceptions a method can throw.</span></span>

<span data-ttu-id="121f9-166">__语法：__</span><span class="sxs-lookup"><span data-stu-id="121f9-166">__Syntax:__</span></span>

```xml
<exception cref="member">description</exception>
```

<span data-ttu-id="121f9-167">__示例：__</span><span class="sxs-lookup"><span data-stu-id="121f9-167">__Example:__</span></span>

```vb
Public Module DataBaseOperations
    ''' <exception cref="MasterFileFormatCorruptException"></exception>
    ''' <exception cref="MasterFileLockedOpenException"></exception>
    Public Sub ReadRecord(flag As Integer)
        If Flag = 1 Then
            Throw New MasterFileFormatCorruptException()
        ElseIf Flag = 2 Then
            Throw New MasterFileLockedOpenException()
        End If
        ' ...
    End Sub
End Module
```

### <a name="ltincludegt"></a><span data-ttu-id="121f9-168">&lt;include&gt;</span><span class="sxs-lookup"><span data-stu-id="121f9-168">&lt;include&gt;</span></span>

<span data-ttu-id="121f9-169">此标记用于包括来自外部格式正确的 XML 文档的信息。</span><span class="sxs-lookup"><span data-stu-id="121f9-169">This tag is used to include information from an external well-formed XML document.</span></span> <span data-ttu-id="121f9-170">XPath 表达式应用于要指定什么 XML 应包含从文档的 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="121f9-170">An XPath expression is applied to the XML document to specify what XML should be included from the document.</span></span> <span data-ttu-id="121f9-171">`<include>`标记然后替换从外部文档中选定的 XML。</span><span class="sxs-lookup"><span data-stu-id="121f9-171">The `<include>` tag is then replaced with the selected XML from the external document.</span></span>

<span data-ttu-id="121f9-172">__语法：__</span><span class="sxs-lookup"><span data-stu-id="121f9-172">__Syntax:__</span></span>

```xml
<include file="filename" path="xpath">
```

<span data-ttu-id="121f9-173">__示例：__</span><span class="sxs-lookup"><span data-stu-id="121f9-173">__Example:__</span></span>

<span data-ttu-id="121f9-174">如果源代码包含如下所示的声明：</span><span class="sxs-lookup"><span data-stu-id="121f9-174">If the source code contained a declaration like the following:</span></span>

```vb
''' <include file="docs.xml" path="extra/class[@name="IntList"]/*" />
```

<span data-ttu-id="121f9-175">外部文件 docs.xml 感到以下内容，并且</span><span class="sxs-lookup"><span data-stu-id="121f9-175">and the external file docs.xml had the following contents</span></span>

```xml
<?xml version="1.0"?>
<extra>
    <class name="IntList">
        <summary>
            Contains a list of integers.
        </summary>
    </class>
    <class name="StringList">
        <summary>
            Contains a list of strings.
        </summary>
    </class>
</extra>
```

<span data-ttu-id="121f9-176">然后同一文档是输出，如同的源代码包含：</span><span class="sxs-lookup"><span data-stu-id="121f9-176">then the same documentation is output as if the source code contained:</span></span>

```xml
''' <summary>
''' Contains a list of integers.
''' </summary>
```

### <a name="ltlistgt"></a><span data-ttu-id="121f9-177">&lt;list&gt;</span><span class="sxs-lookup"><span data-stu-id="121f9-177">&lt;list&gt;</span></span>

<span data-ttu-id="121f9-178">此标记用于创建列表或项的表。</span><span class="sxs-lookup"><span data-stu-id="121f9-178">This tag is used to create a list or table of items.</span></span> <span data-ttu-id="121f9-179">它可能包含`<listheader>`块来定义表或定义列表的标题行。</span><span class="sxs-lookup"><span data-stu-id="121f9-179">It may contain a `<listheader>` block to define the heading row of either a table or definition list.</span></span> <span data-ttu-id="121f9-180">（在定义表时，仅在标题中的术语的项需要提供。）</span><span class="sxs-lookup"><span data-stu-id="121f9-180">(When defining a table, only an entry for term in the heading need be supplied.)</span></span>

<span data-ttu-id="121f9-181">使用指定列表中的每个项`<item>`块。</span><span class="sxs-lookup"><span data-stu-id="121f9-181">Each item in the list is specified with an `<item>` block.</span></span> <span data-ttu-id="121f9-182">创建定义列表时，必须指定术语和说明。</span><span class="sxs-lookup"><span data-stu-id="121f9-182">When creating a definition list, both term and description must be specified.</span></span> <span data-ttu-id="121f9-183">但是，对于表、 项目符号列表或编号的列表，需指定仅说明。</span><span class="sxs-lookup"><span data-stu-id="121f9-183">However, for a table, bulleted list, or numbered list, only description need be specified.</span></span>

<span data-ttu-id="121f9-184">__语法：__</span><span class="sxs-lookup"><span data-stu-id="121f9-184">__Syntax:__</span></span>

```xml
<list type="bullet" | "number" | "table">
    <listheader>
        <term>term</term>
        <description>description</description>
    </listheader>
    <item>
        <term>term</term>
        <description>description</description>
    </item>
    ...
    <item>
        <term>term</term>
        <description>description</description>
    </item>
</list>
```

<span data-ttu-id="121f9-185">__示例：__</span><span class="sxs-lookup"><span data-stu-id="121f9-185">__Example:__</span></span>

```vb
Public Class TestClass
    ''' <remarks>
    ''' Here is an example of a bulleted list:
    ''' <list type="bullet">
    '''     <item>
    '''        <description>Item 1.</description>
    '''     </item>
    '''     <item>
    '''         <description>Item 2.</description>
    '''     </item>
    ''' </list>
    ''' </remarks>
    Public Shared Sub Main()
    End Sub
End Class
```

### <a name="ltparagt"></a><span data-ttu-id="121f9-186">&lt;para&gt;</span><span class="sxs-lookup"><span data-stu-id="121f9-186">&lt;para&gt;</span></span>

<span data-ttu-id="121f9-187">此标记是用于其他标记内，例如`<remarks>`或`<returns>`，并允许结构添加到文本。</span><span class="sxs-lookup"><span data-stu-id="121f9-187">This tag is for use inside other tags, such as `<remarks>` or `<returns>`, and permits structure to be added to text.</span></span>

<span data-ttu-id="121f9-188">__语法：__</span><span class="sxs-lookup"><span data-stu-id="121f9-188">__Syntax:__</span></span>

```xml
<para>content</para>
```

<span data-ttu-id="121f9-189">__示例：__</span><span class="sxs-lookup"><span data-stu-id="121f9-189">__Example:__</span></span>

```vb
''' <summary>
''' This is the entry point of the Point class testing program.
''' <para>This program tests each method and operator, and
''' is intended to be run after any non-trvial maintenance has
''' been performed on the Point class.</para>
''' </summary>
Public Shared Sub Main()
End Sub
```

### <a name="ltparamgt"></a><span data-ttu-id="121f9-190">&lt;param&gt;</span><span class="sxs-lookup"><span data-stu-id="121f9-190">&lt;param&gt;</span></span>

<span data-ttu-id="121f9-191">此标记描述方法、 构造函数或索引的属性的参数。</span><span class="sxs-lookup"><span data-stu-id="121f9-191">This tag describes a parameter for a method, constructor, or indexed property.</span></span>

<span data-ttu-id="121f9-192">__语法：__</span><span class="sxs-lookup"><span data-stu-id="121f9-192">__Syntax:__</span></span>

```xml
<param name="name">description</param>
```

<span data-ttu-id="121f9-193">__示例：__</span><span class="sxs-lookup"><span data-stu-id="121f9-193">__Example:__</span></span>

```vb
''' <summary>
''' This method changes the point's location to the given
''' coordinates.
''' </summary>
''' <param name="x"><c>x</c> is the new x-coordinate.</param>
''' <param name="y"><c>y</c> is the new y-coordinate.</param>
Public Sub Move(x As Integer, y As Integer)
    Me.x = x
    Me.y = y
End Sub
```

### <a name="ltparamrefgt"></a><span data-ttu-id="121f9-194">&lt;paramref&gt;</span><span class="sxs-lookup"><span data-stu-id="121f9-194">&lt;paramref&gt;</span></span>

<span data-ttu-id="121f9-195">此标记指示单词为参数。</span><span class="sxs-lookup"><span data-stu-id="121f9-195">This tag indicates that a word is a parameter.</span></span> <span data-ttu-id="121f9-196">可以处理文档文件以设置此参数的格式以不同的方式。</span><span class="sxs-lookup"><span data-stu-id="121f9-196">The documentation file can be processed to format this parameter in some distinct way.</span></span>

<span data-ttu-id="121f9-197">__语法：__</span><span class="sxs-lookup"><span data-stu-id="121f9-197">__Syntax:__</span></span>

```xml
<paramref name="name"/>
```

<span data-ttu-id="121f9-198">__示例：__</span><span class="sxs-lookup"><span data-stu-id="121f9-198">__Example:__</span></span>

```vb
''' <summary>
''' This constructor initializes the new Point to
''' (<paramref name="x"/>,<paramref name="y"/>).
''' </summary>
''' <param name="x"><c>x</c> is the new Point's x-coordinate.</param>
''' <param name="y"><c>y</c> is the new Point's y-coordinate.</param>
Public Sub New(x As Integer, y As Integer)
    Me.x = x
    Me.y = y
End Sub
```

### <a name="ltpermissiongt"></a><span data-ttu-id="121f9-199">&lt;permission&gt;</span><span class="sxs-lookup"><span data-stu-id="121f9-199">&lt;permission&gt;</span></span>

<span data-ttu-id="121f9-200">此标记记录成员的安全可访问性</span><span class="sxs-lookup"><span data-stu-id="121f9-200">This tag documents the security accessibility of a member</span></span>

<span data-ttu-id="121f9-201">__语法：__</span><span class="sxs-lookup"><span data-stu-id="121f9-201">__Syntax:__</span></span>

```xml
<permission cref="member">description</permission>
```

<span data-ttu-id="121f9-202">__示例：__</span><span class="sxs-lookup"><span data-stu-id="121f9-202">__Example:__</span></span>

```vb
''' <permission cref="System.Security.PermissionSet">Everyone can
''' access this method.</permission>
Public Shared Sub Test()
End Sub
```

### <a name="ltremarksgt"></a><span data-ttu-id="121f9-203">&lt;remarks&gt;</span><span class="sxs-lookup"><span data-stu-id="121f9-203">&lt;remarks&gt;</span></span>

<span data-ttu-id="121f9-204">此标记指定一种类型的概述信息。</span><span class="sxs-lookup"><span data-stu-id="121f9-204">This tag specifies overview information about a type.</span></span> <span data-ttu-id="121f9-205">(使用`<summary>`来描述类型的成员。)</span><span class="sxs-lookup"><span data-stu-id="121f9-205">(Use `<summary>` to describe the members of a type.)</span></span>

<span data-ttu-id="121f9-206">__语法：__</span><span class="sxs-lookup"><span data-stu-id="121f9-206">__Syntax:__</span></span>

```xml
<remarks>description</remarks>
```

<span data-ttu-id="121f9-207">__示例：__</span><span class="sxs-lookup"><span data-stu-id="121f9-207">__Example:__</span></span>

```vb
''' <remarks>
''' Class <c>Point</c> models a point in a two-dimensional plane.
''' </remarks>
Public Class Point 
End Class
```

### <a name="ltreturnsgt"></a><span data-ttu-id="121f9-208">&lt;returns&gt;</span><span class="sxs-lookup"><span data-stu-id="121f9-208">&lt;returns&gt;</span></span>

<span data-ttu-id="121f9-209">此标记描述方法的返回值。</span><span class="sxs-lookup"><span data-stu-id="121f9-209">This tag describes the return value of a method.</span></span>

<span data-ttu-id="121f9-210">__语法：__</span><span class="sxs-lookup"><span data-stu-id="121f9-210">__Syntax:__</span></span>

```xml
<returns>description</returns>
```

<span data-ttu-id="121f9-211">__示例：__</span><span class="sxs-lookup"><span data-stu-id="121f9-211">__Example:__</span></span>

```vb
''' <summary>
''' Report a point's location as a string.
''' </summary>
''' <returns>
''' A string representing a point's location, in the form (x,y), without
''' any leading, training, or embedded whitespace.
''' </returns>
Public Overrides Function ToString() As String
    Return "(" & x & "," & y & ")"
End Sub
```

### <a name="ltseegt"></a><span data-ttu-id="121f9-212">&lt;see&gt;</span><span class="sxs-lookup"><span data-stu-id="121f9-212">&lt;see&gt;</span></span>

<span data-ttu-id="121f9-213">此标记允许用于在文本内指定的链接。</span><span class="sxs-lookup"><span data-stu-id="121f9-213">This tag allows a link to be specified within text.</span></span> <span data-ttu-id="121f9-214">(使用`<seealso>`以指示要在另请参见部分中显示的文本。)</span><span class="sxs-lookup"><span data-stu-id="121f9-214">(Use `<seealso>` to indicate text that is to appear in a See Also section.)</span></span>

<span data-ttu-id="121f9-215">__语法：__</span><span class="sxs-lookup"><span data-stu-id="121f9-215">__Syntax:__</span></span>

```xml
<see cref="member"/>
```

<span data-ttu-id="121f9-216">__示例：__</span><span class="sxs-lookup"><span data-stu-id="121f9-216">__Example:__</span></span>

```vb
''' <summary>
''' This method changes the point's location to the given
''' coordinates.
''' </summary>
''' <see cref="Translate"/>
Public Sub Move(x As Integer, y As Integer)
    Me.x = x
    Me.y = y
End Sub

''' <summary>
''' This method changes the point's location by the given x- and
''' y-offsets.
''' </summary>
''' <see cref="Move"/>
Public Sub Translate(x As Integer, y As Integer)
    Me.x += x
    Me.y += y
End Sub
```

### <a name="ltseealsogt"></a><span data-ttu-id="121f9-217">&lt;seealso&gt;</span><span class="sxs-lookup"><span data-stu-id="121f9-217">&lt;seealso&gt;</span></span>

<span data-ttu-id="121f9-218">此标记生成的项的另请参见部分。</span><span class="sxs-lookup"><span data-stu-id="121f9-218">This tag generates an entry for the See Also section.</span></span> <span data-ttu-id="121f9-219">(使用`<see>`指定从文本中的链接。)</span><span class="sxs-lookup"><span data-stu-id="121f9-219">(Use `<see>` to specify a link from within text.)</span></span>

<span data-ttu-id="121f9-220">__语法：__</span><span class="sxs-lookup"><span data-stu-id="121f9-220">__Syntax:__</span></span>

```xml
<seealso cref="member"/>
```

<span data-ttu-id="121f9-221">__示例：__</span><span class="sxs-lookup"><span data-stu-id="121f9-221">__Example:__</span></span>

```vb
''' <summary>
''' This method determines whether two Points have the same location.
''' </summary>
''' <seealso cref="operator=="/>
''' <seealso cref="operator!="/>
Public Overrides Function Equals(o As Object) As Boolean
    ' ...
End Function
```

### <a name="ltsummarygt"></a><span data-ttu-id="121f9-222">&lt;summary&gt;</span><span class="sxs-lookup"><span data-stu-id="121f9-222">&lt;summary&gt;</span></span>

<span data-ttu-id="121f9-223">此标记描述一个类型成员。</span><span class="sxs-lookup"><span data-stu-id="121f9-223">This tag describes a type member.</span></span> <span data-ttu-id="121f9-224">(使用`<remarks>`描述类型本身。)</span><span class="sxs-lookup"><span data-stu-id="121f9-224">(Use `<remarks>` to describe a type itself.)</span></span>

<span data-ttu-id="121f9-225">__语法：__</span><span class="sxs-lookup"><span data-stu-id="121f9-225">__Syntax:__</span></span>

```xml
<summary>description</summary>
```

<span data-ttu-id="121f9-226">__示例：__</span><span class="sxs-lookup"><span data-stu-id="121f9-226">__Example:__</span></span>

```vb
''' <summary>
''' This constructor initializes the new Point to (0,0).
''' </summary>
Public Sub New()
    Me.New(0,0)
End Sub
```

### <a name="lttypeparamgt"></a><span data-ttu-id="121f9-227">&lt;typeparam&gt;</span><span class="sxs-lookup"><span data-stu-id="121f9-227">&lt;typeparam&gt;</span></span>

<span data-ttu-id="121f9-228">此标记描述类型参数。</span><span class="sxs-lookup"><span data-stu-id="121f9-228">This tag describes a type parameter.</span></span>

<span data-ttu-id="121f9-229">__语法：__</span><span class="sxs-lookup"><span data-stu-id="121f9-229">__Syntax:__</span></span>

```xml
<typeparam name="name">description</typeparam>
```

<span data-ttu-id="121f9-230">__示例：__</span><span class="sxs-lookup"><span data-stu-id="121f9-230">__Example:__</span></span>

```vb
''' <typeparam name="T">
''' The base item type. Must implement IComparable.
''' </typeparam>
Public Class ItemManager(Of T As IComparable)
End Class
```

### <a name="ltvaluegt"></a><span data-ttu-id="121f9-231">&lt;value&gt;</span><span class="sxs-lookup"><span data-stu-id="121f9-231">&lt;value&gt;</span></span>

<span data-ttu-id="121f9-232">此标记描述的属性。</span><span class="sxs-lookup"><span data-stu-id="121f9-232">This tag describes a property.</span></span>

<span data-ttu-id="121f9-233">__语法：__</span><span class="sxs-lookup"><span data-stu-id="121f9-233">__Syntax:__</span></span>

```xml
<value>property description</value>
```

<span data-ttu-id="121f9-234">__示例：__</span><span class="sxs-lookup"><span data-stu-id="121f9-234">__Example:__</span></span>

```vb
''' <value>
''' Property <c>X</c> represents the point's x-coordinate.
''' </value>
Public Property X() As Integer
    Get
        Return _x
    End Get
    Set (Value As Integer)
        _x = Value
    End Set
End Property
```

## <a name="id-strings"></a><span data-ttu-id="121f9-235">ID 字符串</span><span class="sxs-lookup"><span data-stu-id="121f9-235">ID Strings</span></span>

<span data-ttu-id="121f9-236">在生成文档文件时，编译器将生成的标记为唯一标识它的文档注释的源代码中每个元素的 ID 字符串。</span><span class="sxs-lookup"><span data-stu-id="121f9-236">When generating the documentation file, the compiler generates an ID string for each element in the source code that is tagged with a documentation comment that uniquely identifies it.</span></span> <span data-ttu-id="121f9-237">此 ID 字符串可以由外部工具，用于标识中编译的程序集的哪个元素对应的文档注释。</span><span class="sxs-lookup"><span data-stu-id="121f9-237">This ID string can be used by external tools to identify which element in a compiled assembly corresponds to the document comment.</span></span>

<span data-ttu-id="121f9-238">按如下所示生成 ID 字符串：</span><span class="sxs-lookup"><span data-stu-id="121f9-238">ID strings are generated as follows:</span></span>

<span data-ttu-id="121f9-239">字符串不得包含空格。</span><span class="sxs-lookup"><span data-stu-id="121f9-239">No white space is placed in the string.</span></span>

<span data-ttu-id="121f9-240">字符串的第一部分标识成员记录，通过单个跟一个冒号字符的类型。</span><span class="sxs-lookup"><span data-stu-id="121f9-240">The first part of the string identifies the kind of member being documented, via a single character followed by a colon.</span></span> <span data-ttu-id="121f9-241">定义了以下类型的成员，则在它后面的括号中的相应字符： 事件 (E) 字段 (F)，包括构造函数和运算符 (M)、 命名空间 (N)、 属性 (P) 和 (T) 类型的方法。</span><span class="sxs-lookup"><span data-stu-id="121f9-241">The following kinds of members are defined, with the corresponding character in parenthesis after it: events (E), fields (F), methods including constructors and operators (M), namespaces (N), properties (P) and types (T).</span></span> <span data-ttu-id="121f9-242">感叹号 （！） 指示字符串的其余部分提供了有关错误的信息和生成 ID 字符串时出错。</span><span class="sxs-lookup"><span data-stu-id="121f9-242">An exclamation point (!) indicates an error occurred while generating the ID string, and the rest of the string provides information about the error.</span></span>

<span data-ttu-id="121f9-243">字符串的第二部分是开始全局命名空间的元素的完全限定的名称。</span><span class="sxs-lookup"><span data-stu-id="121f9-243">The second part of the string is the fully qualified name of the element, starting at the global namespace.</span></span> <span data-ttu-id="121f9-244">用句点分隔的元素，其包含的类型和命名空间名称。</span><span class="sxs-lookup"><span data-stu-id="121f9-244">The name of the element, its enclosing type(s), and namespace are separated by periods.</span></span> <span data-ttu-id="121f9-245">如果项本身的名称包含句点，它们替换为井号 （#）。</span><span class="sxs-lookup"><span data-stu-id="121f9-245">If the name of the item itself has periods, they are replaced by the pound sign (#).</span></span> <span data-ttu-id="121f9-246">（假定没有任何元素的名称中包含此字符。）具有类型参数的类型的名称结尾反引号 （'） 后跟一个数字，表示类型的类型参数的数目。</span><span class="sxs-lookup"><span data-stu-id="121f9-246">(It is assumed that no element has this character in its name.) The name of a type with type parameters ends with a backquote (\`) followed by a number that represents the number of type parameters on the type.</span></span> <span data-ttu-id="121f9-247">务必要记住的因为嵌套的类型有权访问包含这些类型的类型参数、 嵌套的类型隐式包含其包含类型的类型参数和这些类型以在其类型参数总计的计数用例。</span><span class="sxs-lookup"><span data-stu-id="121f9-247">It is important to remember that because nested types have access to the type parameters of the types containing them, nested types implicitly contain the type parameters of their containing types, and those types are counted in their type parameter totals in this case.</span></span>

<span data-ttu-id="121f9-248">对于方法和属性使用的参数，参数列表如下所示，括在括号中。</span><span class="sxs-lookup"><span data-stu-id="121f9-248">For methods and properties with arguments, the argument list follows, enclosed in parentheses.</span></span> <span data-ttu-id="121f9-249">对于不带参数，则省略括号。</span><span class="sxs-lookup"><span data-stu-id="121f9-249">For those without arguments, the parentheses are omitted.</span></span> <span data-ttu-id="121f9-250">确保自变量之间用逗号分隔。</span><span class="sxs-lookup"><span data-stu-id="121f9-250">The arguments are separated by commas.</span></span> <span data-ttu-id="121f9-251">每个自变量的编码是 CLI 签名相同，如下所示： 参数由其完全限定名称。</span><span class="sxs-lookup"><span data-stu-id="121f9-251">The encoding of each argument is the same as a CLI signature, as follows: Arguments are represented by their fully qualified name.</span></span> <span data-ttu-id="121f9-252">例如，`Integer`变得`System.Int32`，`String`变得`System.String`，`Object`变得`System.Object`，依次类推。</span><span class="sxs-lookup"><span data-stu-id="121f9-252">For example, `Integer` becomes `System.Int32`, `String` becomes `System.String`, `Object` becomes `System.Object`, and so on.</span></span> <span data-ttu-id="121f9-253">自变量具有`ByRef`修饰符有 @ 按照其类型名称。</span><span class="sxs-lookup"><span data-stu-id="121f9-253">Arguments having the `ByRef` modifier have a '@' following their type name.</span></span> <span data-ttu-id="121f9-254">参数具有`ByVal`，`Optional`或`ParamArray`修饰符有没有特殊表示法。</span><span class="sxs-lookup"><span data-stu-id="121f9-254">Arguments having the `ByVal`, `Optional` or `ParamArray` modifier have no special notation.</span></span> <span data-ttu-id="121f9-255">参数是数组表示为`[lowerbound:size, ..., lowerbound:size]`其中逗号的数量是秩-1，和的下限和大小的每个维度，以十进制表示如果已知。</span><span class="sxs-lookup"><span data-stu-id="121f9-255">Arguments that are arrays are represented as `[lowerbound:size, ..., lowerbound:size]` where the number of commas is the rank - 1, and the lower bounds and size of each dimension, if known, are represented in decimal.</span></span> <span data-ttu-id="121f9-256">如果未指定下限或大小，则省略它。</span><span class="sxs-lookup"><span data-stu-id="121f9-256">If a lower bound or size is not specified, it is omitted.</span></span> <span data-ttu-id="121f9-257">如果省略某个特定维度的下限和大小，也会省略“:”。</span><span class="sxs-lookup"><span data-stu-id="121f9-257">If the lower bound and size for a particular dimension are omitted, the ':' is omitted as well.</span></span> <span data-ttu-id="121f9-258">一个表示数组的数组"`[]`"每个级别。</span><span class="sxs-lookup"><span data-stu-id="121f9-258">Arrays of arrays are represented by one "`[]`" per level.</span></span>

### <a name="id-string-examples"></a><span data-ttu-id="121f9-259">ID 字符串示例</span><span class="sxs-lookup"><span data-stu-id="121f9-259">ID string examples</span></span>

<span data-ttu-id="121f9-260">下面的示例分别演示 VB 代码，以及从支持的文档注释每个源元素生成的 ID 字符串的片段：</span><span class="sxs-lookup"><span data-stu-id="121f9-260">The following examples each show a fragment of VB code, along with the ID string produced from each source element capable of having a documentation comment:</span></span>

<span data-ttu-id="121f9-261">类型表示使用其完全限定的名称。</span><span class="sxs-lookup"><span data-stu-id="121f9-261">Types are represented using their fully qualified name.</span></span>

```vb
Enum Color
    Red
    Blue
    Green
End Enum

Namespace Acme
    Interface IProcess
    End Interface

    Structure ValueType
        ...
    End Structure

    Class Widget
        Public Class NestedClass
        End Class

        Public Interface IMenuItem
        End Interface

        Public Delegate Sub Del(i As Integer)

        Public Enum Direction
            North
            South
            East
            West
        End Enum
    End Class
End Namespace

"T:Color"
"T:Acme.IProcess"
"T:Acme.ValueType"
"T:Acme.Widget"
"T:Acme.Widget.NestedClass"
"T:Acme.Widget.IMenuItem"
"T:Acme.Widget.Del"
"T:Acme.Widget.Direction"
```

<span data-ttu-id="121f9-262">字段由其完全限定名称表示。</span><span class="sxs-lookup"><span data-stu-id="121f9-262">Fields are represented by their fully qualified name.</span></span>

```vb
Namespace Acme
    Structure ValueType
        Private total As Integer
    End Structure

    Class Widget
        Public Class NestedClass
            Private value As Integer
        End Class

        Private message As String
        Private Shared defaultColor As Color
        Private Const PI As Double = 3.14159
        Protected ReadOnly monthlyAverage As Double
        Private array1() As Long
        Private array2(,) As Widget
    End Class
End Namespace

"F:Acme.ValueType.total"
"F:Acme.Widget.NestedClass.value"
"F:Acme.Widget.message"
"F:Acme.Widget.defaultColor"
"F:Acme.Widget.PI"
"F:Acme.Widget.monthlyAverage"
"F:Acme.Widget.array1"
"F:Acme.Widget.array2"
```

<span data-ttu-id="121f9-263">构造函数。</span><span class="sxs-lookup"><span data-stu-id="121f9-263">Constructors.</span></span>

```vb
Namespace Acme
    Class Widget
        Shared Sub New()
        End Sub

        Public Sub New()
        End Sub

        Public Sub New(s As String)
        End Sub
    End Class
End Namespace

"M:Acme.Widget.#cctor"
"M:Acme.Widget.#ctor"
"M:Acme.Widget.#ctor(System.String)"
```

<span data-ttu-id="121f9-264">方法。</span><span class="sxs-lookup"><span data-stu-id="121f9-264">Methods.</span></span>

```vb
Namespace Acme
    Structure ValueType
        Public Sub M(i As Integer)
        End Sub
    End Structure

    Class Widget
        Public Class NestedClass
            Public Sub M(i As Integer)
            End Sub
        End Class

        Public Shared Sub M0()
        End Sub

        Public Sub M1(c As Char, ByRef f As Float, _
            ByRef v As ValueType)
        End Sub

        Public Sub M2(x1() As Short, x2(,) As Integer, _
            x3()() As Long)
        End Sub

        Public Sub M3(x3()() As Long, x4()(,,) As Widget)
        End Sub

        Public Sub M4(Optional i As Integer = 1)

        Public Sub M5(ParamArray args() As Object)
        End Sub
    End Class
End Namespace

"M:Acme.ValueType.M(System.Int32)"
"M:Acme.Widget.NestedClass.M(System.Int32)"
"M:Acme.Widget.M0"
"M:Acme.Widget.M1(System.Char,System.Single@,Acme.ValueType@)"
"M:Acme.Widget.M2(System.Int16[],System.Int32[0:,0:],System.Int64[][])"
"M:Acme.Widget.M3(System.Int64[][],Acme.Widget[0:,0:,0:][])"
"M:Acme.Widget.M4(System.Int32)"
"M:Acme.Widget.M5(System.Object[])"
```

<span data-ttu-id="121f9-265">属性。</span><span class="sxs-lookup"><span data-stu-id="121f9-265">Properties.</span></span>

```vb
Namespace Acme
    Class Widget
        Public Property Width() As Integer
            Get
            End Get
            Set (Value As Integer)
            End Set
        End Property

        Public Default Property Item(i As Integer) As Integer
            Get
            End Get
            Set (Value As Integer)
            End Set
        End Property

        Public Default Property Item(s As String, _
            i As Integer) As Integer
            Get
            End Get
            Set (Value As Integer)
            End Set
        End Property
    End Class
End Namespace

"P:Acme.Widget.Width"
"P:Acme.Widget.Item(System.Int32)"
"P:Acme.Widget.Item(System.String,System.Int32)"
```

<span data-ttu-id="121f9-266">事件</span><span class="sxs-lookup"><span data-stu-id="121f9-266">Events</span></span>   

```vb
Namespace Acme
    Class Widget
        Public Event AnEvent As EventHandler
        Public Event AnotherEvent()
    End Class
End Namespace

"E:Acme.Widget.AnEvent"
"E:Acme.Widget.AnotherEvent"
```

<span data-ttu-id="121f9-267">运算符。</span><span class="sxs-lookup"><span data-stu-id="121f9-267">Operators.</span></span>

```vb
Namespace Acme
    Class Widget
        Public Shared Operator +(x As Widget) As Widget
        End Operator

        Public Shared Operator +(x1 As Widget, x2 As Widget) As Widget
        End Operator
    End Class
End Namespace

"M:Acme.Widget.op_UnaryPlus(Acme.Widget)"
"M:Acme.Widget.op_Addition(Acme.Widget,Acme.Widget)"
```

<span data-ttu-id="121f9-268">转换运算符具有一个尾随`~`跟的返回类型。</span><span class="sxs-lookup"><span data-stu-id="121f9-268">Conversion operators have a trailing `~` followed by the return type.</span></span>

```vb
Namespace Acme
    Class Widget
        Public Shared Narrowing Operator CType(x As Widget) As _
            Integer
        End Operator

        Public Shared Widening Operator CType(x As Widget) As Long
        End Operator
    End Class
End Namespace

"M:Acme.Widget.op_Explicit(Acme.Widget)~System.Int32"
"M:Acme.Widget.op_Implicit(Acme.Widget)~System.Int64"
```

## <a name="documentation-comments-example"></a><span data-ttu-id="121f9-269">文档注释示例</span><span class="sxs-lookup"><span data-stu-id="121f9-269">Documentation comments example</span></span>

<span data-ttu-id="121f9-270">下面的示例显示了源代码`Point`类：</span><span class="sxs-lookup"><span data-stu-id="121f9-270">The following example shows the source code of a `Point` class:</span></span>

```vb
Namespace Graphics
    ''' <remarks>
    ''' Class <c>Point</c> models a point in a two-dimensional
    ''' plane.
    ''' </remarks>
    Public Class Point
        ''' <summary>
        ''' Instance variable <c>x</c> represents the point's x-coordinate.
        ''' </summary>
        Private _x As Integer

        ''' <summary>
        ''' Instance variable <c>y</c> represents the point's y-coordinate.
        ''' </summary>
        Private _y As Integer

        ''' <value>
        ''' Property <c>X</c> represents the point's x-coordinate.
        ''' </value>
        Public Property X() As Integer
            Get
                Return _x
            End Get
            Set(Value As Integer)
                _x = Value
            End Set
        End Property

        ''' <value>
        ''' Property <c>Y</c> represents the point's y-coordinate.
        ''' </value>
        Public Property Y() As Integer
            Get
                Return _y
            End Get
            Set(Value As Integer)
                _y = Value
            End Set
        End Property

        ''' <summary>
        ''' This constructor initializes the new Point to (0,0).
        ''' </summary>
        Public Sub New()
            Me.New(0, 0)
        End Sub

        ''' <summary>
        ''' This constructor initializes the new Point to
        ''' (<paramref name="x"/>,<paramref name="y"/>).
        ''' </summary>
        ''' <param name="x"><c>x</c> is the new Point's
        ''' x-coordinate.</param>
        ''' <param name="y"><c>y</c> is the new Point's
        ''' y-coordinate.</param>
        Public Sub New(x As Integer, y As Integer)
            Me.X = x
            Me.Y = y
        End Sub

        ''' <summary>
        ''' This method changes the point's location to the given
        ''' coordinates.
        ''' </summary>
        ''' <param name="x"><c>x</c> is the new x-coordinate.</param>
        ''' <param name="y"><c>y</c> is the new y-coordinate.</param>
        ''' <see cref="Translate"/>
        Public Sub Move(x As Integer, y As Integer)
            Me.X = x
            Me.Y = y
        End Sub

        ''' <summary>
        ''' This method changes the point's location by the given x- and
        ''' y-offsets.
        ''' <example>
        ''' For example:
        ''' <code>
        '''    Dim p As Point = New Point(3, 5)
        '''    p.Translate(-1, 3)
        ''' </code>
        ''' results in <c>p</c>'s having the value (2,8).
        ''' </example>
        ''' </summary>
        ''' <param name="x"><c>x</c> is the relative x-offset.</param>
        ''' <param name="y"><c>y</c> is the relative y-offset.</param>
        ''' <see cref="Move"/>
        Public Sub Translate(x As Integer, y As Integer)
            Me.X += x
            Me.Y += y
        End Sub

        ''' <summary>
        ''' This method determines whether two Points have the same
        ''' location.
        ''' </summary>
        ''' <param name="o"><c>o</c> is the object to be compared to the
        ''' current object.</param>
        ''' <returns>
        ''' True if the Points have the same location and they have the
        ''' exact same type; otherwise, false.
        ''' </returns>
        ''' <seealso cref="Operator op_Equality"/>
        ''' <seealso cref="Operator op_Inequality"/>
        Public Overrides Function Equals(o As Object) As Boolean
            If o Is Nothing Then
                Return False
            End If
            If o Is Me Then
                Return True
            End If
            If Me.GetType() Is o.GetType() Then
                Dim p As Point = CType(o, Point)
                Return (X = p.X) AndAlso (Y = p.Y)
            End If
            Return False
        End Function

        ''' <summary>
        ''' Report a point's location as a string.
        ''' </summary>
        ''' <returns>
        ''' A string representing a point's location, in the form
        ''' (x,y), without any leading, training, or embedded whitespace.
        ''' </returns>
        Public Overrides Function ToString() As String
            Return "(" & X & "," & Y & ")"
        End Function

        ''' <summary>
        ''' This operator determines whether two Points have the
        ''' same location.
        ''' </summary>
        ''' <param name="p1"><c>p1</c> is the first Point to be compared.
        ''' </param>
        ''' <param name="p2"><c>p2</c> is the second Point to be compared.
        ''' </param>
        ''' <returns>
        ''' True if the Points have the same location and they 
        ''' have the exact same type; otherwise, false.
        ''' </returns>
        ''' <seealso cref="Equals"/>
        ''' <seealso cref="op_Inequality"/>
        Public Shared Operator =(p1 As Point, p2 As Point) As Boolean
            If p1 Is Nothing OrElse p2 Is Nothing Then
                Return False
            End If
            If p1.GetType() Is p2.GetType() Then
                Return (p1.X = p2.X) AndAlso (p1.Y = p2.Y)
            End If
            Return False
        End Operator

        ''' <summary>
        ''' This operator determines whether two Points have the
        ''' same location.
        ''' </summary>
        ''' <param name="p1"><c>p1</c> is the first Point to be comapred.
        ''' </param>
        ''' <param name="p2"><c>p2</c> is the second Point to be compared.
        ''' </param>
        ''' <returns>
        ''' True if the Points do not have the same location and
        ''' the exact same type; otherwise, false.
        ''' </returns>
        ''' <seealso cref="Equals"/>
        ''' <seealso cref="op_Equality"/>
        Public Shared Operator <>(p1 As Point, p2 As Point) As Boolean
            Return Not p1 = p2
        End Operator

        ''' <summary>
        ''' This is the entry point of the Point class testing program.
        ''' <para>This program tests each method and operator, and
        ''' is intended to be run after any non-trvial maintenance has
        ''' been performed on the Point class.</para>
        ''' </summary>
        Public Shared Sub Main()
            ' class test code goes here
        End Sub
    End Class
End Namespace
```

<span data-ttu-id="121f9-271">下面是当给定类的源代码时生成的输出`Point`，上面所示：</span><span class="sxs-lookup"><span data-stu-id="121f9-271">Here is the output produced when given the source code for class `Point`, shown above:</span></span>

```xml
<?xml version="1.0"?>
<doc>
    <assembly>
        <name>Point</name>
    </assembly>
    <members>
        <member name="T:Graphics.Point">
            <remarks>Class <c>Point</c> models a point in a
            two-dimensional plane. </remarks>
        </member>
        <member name="F:Graphics.Point.x">
            <summary>Instance variable <c>x</c> represents the point's
            x-coordinate.</summary>
        </member>
        <member name="F:Graphics.Point.y">
            <summary>Instance variable <c>y</c> represents the point's
            y-coordinate.</summary>
        </member>
        <member name="M:Graphics.Point.#ctor">
            <summary>This constructor initializes the new Point to
            (0,0).</summary>
        </member>
        <member name="M:Graphics.Point.#ctor(System.Int32,System.Int32)">
            <summary>This constructor initializes the new Point to
            (<paramref name="x"/>,<paramref name="y"/>).</summary>
            <param><c>x</c> is the new Point's x-coordinate.</param>
            <param><c>y</c> is the new Point's y-coordinate.</param>
        </member>
        <member name="M:Graphics.Point.Move(System.Int32,System.Int32)">
            <summary>This method changes the point's location to
            the given coordinates.</summary>
            <param><c>x</c> is the new x-coordinate.</param>
            <param><c>y</c> is the new y-coordinate.</param>
            <see cref=
            "M:Graphics.Point.Translate(System.Int32,System.Int32)"/>
        </member>
        <member name=
        "M:Graphics.Point.Translate(System.Int32,System.Int32)">
            <summary>This method changes the point's location by the given
            x- and y-offsets.
            <example>For example:
            <code>
            Point p = new Point(3,5);
            p.Translate(-1,3);
            </code>
            results in <c>p</c>'s having the value (2,8).
            </example>
            </summary>
            <param><c>x</c> is the relative x-offset.</param>
            <param><c>y</c> is the relative y-offset.</param>
            <see cref="M:Graphics.Point.Move(System.Int32,System.Int32)"/>
        </member>
        <member name="M:Graphics.Point.Equals(System.Object)">
            <summary>This method determines whether two Points have the
            same location.</summary>
            <param><c>o</c> is the object to be compared to the current
            object.</param>
            <returns>True if the Points have the same location and they
            have the exact same type; otherwise, false.</returns>
            <seealso cref=
            "M:Graphics.Point.op_Equality(Graphics.Point,Graphics.Point)"
            />
            <seealso cref=
           "M:Graphics.Point.op_Inequality(Graphics.Point,Graphics.Point)"
            />
        </member>
        <member name="M:Graphics.Point.ToString">
            <summary>Report a point's location as a string.</summary>
            <returns>A string representing a point's location, in the form
            (x,y), without any leading, training, or embedded
            whitespace.</returns>
        </member>
        <member name=
        "M:Graphics.Point.op_Equality(Graphics.Point,Graphics.Point)">
            <summary>This operator determines whether two Points have the
            same location.</summary>
            <param><c>p1</c> is the first Point to be compared.</param>
            <param><c>p2</c> is the second Point to be compared.</param>
            <returns>True if the Points have the same location and they
            have the exact same type; otherwise, false.</returns>
            <seealso cref="M:Graphics.Point.Equals(System.Object)"/>
            <seealso cref=
           "M:Graphics.Point.op_Inequality(Graphics.Point,Graphics.Point)"
            />
        </member>
        <member name=
        "M:Graphics.Point.op_Inequality(Graphics.Point,Graphics.Point)">
            <summary>This operator determines whether two Points have the
            same location.</summary>
            <param><c>p1</c> is the first Point to be compared.</param>
            <param><c>p2</c> is the second Point to be compared.</param>
            <returns>True if the Points do not have the same location and
            the exact same type; otherwise, false.</returns>
            <seealso cref="M:Graphics.Point.Equals(System.Object)"/>
            <seealso cref=
            "M:Graphics.Point.op_Equality(Graphics.Point,Graphics.Point)"
            />
        </member>
        <member name="M:Graphics.Point.Main">
            <summary>This is the entry point of the Point class testing
            program.
            <para>This program tests each method and operator, and
            is intended to be run after any non-trvial maintenance has
            been performed on the Point class.</para>
            </summary>
        </member>
        <member name="P:Graphics.Point.X">
            <value>Property <c>X</c> represents the point's
            x-coordinate.</value>
        </member>
        <member name="P:Graphics.Point.Y">
            <value>Property <c>Y</c> represents the point's
            y-coordinate.</value>
        </member>
    </members>
</doc>
```