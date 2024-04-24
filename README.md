<pre lang=vb.net>
Module Module1

    Sub Main()
        Console.WriteLine(ValidPwdFormatCheck("abc123"))
        Console.WriteLine(Authenticated("Bob", "letmen"))
        Console.WriteLine(Authenticated2D("Bob", "letmein"))
    End Sub
    ' Be able to write simple data validation routines.
    'checking if an entered string has a
    'minimum length
    Function StringMinLength(input As String, lengthRequired As Integer) As Boolean
        If input.Length < lengthRequired Then
            Return False
        End If
        Return True
    End Function

    ' Checking if a string is empty
    Function isStringEmpty(input As String) As Boolean
        If input.Length = 0 Then
            Return True
        End If
        Return False
    End Function

    ' checking if data entered lies within a given range
    ' e.g. between 1 and 10
    Function rangeCheck(input As Integer, lower As Integer, upper As Integer) As Boolean
        If input >= lower And input <= upper Then
            Return True
        End If
        Return False
    End Function

    ' Other validation functions
    Function ContainsChar(input As String, charToCheck As Char) As Boolean
        If input.Contains(charToCheck) Then
            Return True
        End If
        Return False
    End Function
    ' Check a string contains
    ' at least
    ' one upper case
    ' one lower case
    ' one number
    ' at least 8 characters
    Function ValidPwdFormatCheck(input As String) As Boolean
        If Not StringMinLength(input, 8) Then
            Return False
        End If
        Dim containsUpper, containsLower, containsNumber As Boolean
        For Each c In input
            If Asc(c) >= Asc("A") And Asc(c) <= Asc("Z") Then
                containsUpper = True
            End If
            If Asc(c) >= Asc("a") And Asc(c) <= Asc("z") Then
                containsLower = True
            End If
            If IsNumeric(Val(c)) Then
                containsNumber = True
            End If
        Next
        Return containsUpper And containsNumber And containsLower

    End Function

    ' Be able to write simple authentication routines
    Function Authenticated(username As String, password As String) As Boolean
        Dim usernames As String() = {"Bob", "Bill", "Betty"}
        Dim passwords As String() = {"letmein", "123456", "password"}
        Dim index As Integer = 0
        While index < usernames.Length
            If usernames(index) = username And passwords(index) = password Then
                Return True
            End If
            index += 1
        End While
        Return False
    End Function

    Function Authenticated2D(username As String, password As String) As Boolean
        Dim userNamePwds As String(,) = {{"Bob", "Bill", "Betty"}, {"letmein", "123456", "password"}}
        For i = 0 To userNamePwds.GetLength(0)
            If userNamePwds(0, i) = username And userNamePwds(1, i) = password Then
                Return True
            End If
        Next
        Return False
    End Function

End Module
