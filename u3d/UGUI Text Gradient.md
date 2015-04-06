2015.4.6		初次提交

对于UGUI Text 没有渐变字体，相信困扰不少人。
但我相信UGUI不提供这些，让我们自己去扩展，从另外一些方面来，是更好的，更合理的。
UGUI保持其简单。让其他人上手快，而且很轻盈，我真希望能一直这么保持下去，不要为了加新的特性支持，导致其越来越臃肿。

好了，废话不多说了。先来看看我做的效果：
![Text2效果图](http://img.blog.csdn.net/20150406202017125)

网络上，外国也有人放出了一些实现的方式，我看了最好的是：
https://github.com/WestHillApps/uGUI-Effect-Tool
这是一个脱离Text实现的渲染方式。
整个区域地进行渐变

好了，既然说上面是脱离Text实现的，那我就来个继承Text实现的。现在命名为Text2

先说说原理：
**一个字分2个面，4个顶点，左上0，右上1，右下2，左下3......**

不知道你能不能理解，反正我对图形学不懂，就不敢装了！

直接上代码吧：

```
using System;
using System.Collections.Generic;

namespace UnityEngine.UI
{
    [AddComponentMenu("UI/Text2", 11)]
    public class Text2 : Text
    {
        public Color m_BottomColor = Color.red;

        /// <summary>
        /// Draw the Text.
        /// </summary>
        protected override void OnFillVBO(List<UIVertex> vbo)
        {
            if (font == null)
                return;

            base.OnFillVBO(vbo);

            var index = 0;
            for (var i = 0; i < vbo.Count;  ++i)
            {
                //一个字分2个面，4个顶点，左上0，右上1，右下2，左下3......
                index = i % 4;
                if(index >= 2)
                {
                    var v = vbo[i];
                    v.color = m_BottomColor;
                    vbo[i] = v;
                }
            }
        }
    }

    
}

```

还有它的编辑类：

```
using UnityEngine;
using UnityEngine.UI;

namespace UnityEditor.UI
{
    [CustomEditor(typeof(Text2), true)]
    [CanEditMultipleObjects]
    public class Text2Editor : GraphicEditor
    {
        SerializedProperty m_Text;
        SerializedProperty m_FontData;
        SerializedProperty m_BottomColor;

        protected override void OnEnable()
        {
            base.OnEnable();
            m_Text = serializedObject.FindProperty("m_Text");
            m_FontData = serializedObject.FindProperty("m_FontData");
            m_BottomColor = serializedObject.FindProperty("m_BottomColor");
        }

        public override void OnInspectorGUI()
        {
            serializedObject.Update();

            EditorGUILayout.PropertyField(m_Text);
            EditorGUILayout.PropertyField(m_FontData);
            EditorGUILayout.PropertyField(m_Color);
            EditorGUILayout.PropertyField(m_BottomColor);
            EditorGUILayout.PropertyField(m_Material);

            serializedObject.ApplyModifiedProperties();
        }
    }
}
```


以上是我团队研究的成果，转载请注明原文链接
