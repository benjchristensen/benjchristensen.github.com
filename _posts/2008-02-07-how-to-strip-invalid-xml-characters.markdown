---
author: benjchristensen
comments: true
date: 2008-02-07 01:30:01+00:00
layout: post
slug: how-to-strip-invalid-xml-characters
title: How to strip invalid XML characters
wordpress_id: 54
categories:
- Code
---

http://cse-mjmcl.cse.bris.ac.uk/blog/2007/02/14/1171465494443.html   

  /**

     * This method ensures that the output String has only

     * valid XML unicode characters as specified by the

     * XML 1.0 standard. For reference, please see

     * <a href="http://www.w3.org/TR/2000/REC-xml-20001006#NT-Char">the

     * standard</a>. This method will return an empty

     * String if the input is null or empty.

     *

     * @param in The String whose non-valid characters we want to remove.

     * @return The in String, stripped of non-valid characters.

     */

    public String stripNonValidXMLCharacters(String in) {

        StringBuffer out = new StringBuffer(); // Used to hold the output.

        char current; // Used to reference the current character.

  


        if (in == null || ("".equals(in))) return ""; // vacancy test.

        for (int i = 0; i < in.length(); i++) {

            current = in.charAt(i); // NOTE: No IndexOutOfBoundsException caught here; it should not happen.

            if ((current == 0x9) ||

                (current == 0xA) ||

                (current == 0xD) ||

                ((current >= 0x20) && (current <= 0xD7FF)) ||

                ((current >= 0xE000) && (current <= 0xFFFD)) ||

                ((current >= 0x10000) && (current <= 0x10FFFF)))

                out.append(current);

        }

        return out.toString();

    }     
