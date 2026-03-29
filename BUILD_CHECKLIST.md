# 📋 Build & Test Checklist

## Pre-Build Checklist

### ✅ Backend Setup
- [ ] Backend server is running at `http://localhost:5001`
- [ ] MongoDB is running
- [ ] Database is seeded with test accounts
- [ ] Backend console shows "Server running on port 5001"

**Commands:**
```powershell
cd c:\Users\SAHIL\AndroidStudioProjects\campusHelper\backend
npm install
npm start

# In another terminal (if needed):
node src/seeders/seedData.js
```

### ✅ Android Studio Setup
- [ ] Android Studio is open
- [ ] Project `CampusHelper2` is loaded
- [ ] Gradle sync completed successfully
- [ ] No build errors in Build tab
- [ ] Emulator is running OR device is connected

---

## Build Steps

### 1. Clean Build
```powershell
cd c:\Users\SAHIL\AndroidStudioProjects\campusHelper\CampusHelper2
./gradlew clean
```

### 2. Build Project
- Click: **Build → Rebuild Project**
- OR: `./gradlew build`
- Wait for: "BUILD SUCCESSFUL"

### 3. Run App
- Click: **Run → Run 'app'** (Shift+F10)
- Select target device/emulator
- Wait for app to install and launch

---

## Testing Checklist

### ✅ Authentication Flow
- [ ] App shows splash screen
- [ ] Navigate to login screen
- [ ] Enter: `student@test.com` / `password123`
- [ ] Click "Login"
- [ ] Redirects to Student Dashboard
- [ ] Bottom navigation shows 5 tabs

### ✅ Home Tab - Subjects
- [ ] Subjects load automatically
- [ ] Subjects displayed in grid layout
- [ ] Each subject card shows name and code
- [ ] Swipe down to refresh works
- [ ] Click a subject → Navigate to details

### ✅ Subject Detail
- [ ] Toolbar shows subject name
- [ ] "Practice Test" button visible
- [ ] Materials list displays (if any)
- [ ] Floating chat button (bottom-right) visible
- [ ] Click chat button → Open AI chat

### ✅ AI Chatbot
- [ ] Chat screen opens with toolbar
- [ ] Message input field at bottom
- [ ] Send button visible
- [ ] Type: "What is photosynthesis?"
- [ ] Click send
- [ ] Message appears in chat
- [ ] AI response appears after ~2 seconds
- [ ] Timestamp displays correctly

### ✅ Practice Test
- [ ] Click "Practice Test" in subject detail
- [ ] Loading indicator shows
- [ ] Test screen loads with first question
- [ ] Question number shows (Question 1 of 10)
- [ ] 4 radio button options display
- [ ] Select an answer
- [ ] Click "Next" → Move to question 2
- [ ] Click "Previous" → Back to question 1
- [ ] Answer all 10 questions
- [ ] "Submit" button appears on last question
- [ ] Click "Submit"

### ✅ Test Results
- [ ] Results screen displays
- [ ] Score percentage shows prominently
- [ ] Grade (A+, A, B, C, D, F) displays
- [ ] Total questions count correct
- [ ] Correct answers count correct
- [ ] Incorrect answers count correct
- [ ] Score color matches performance (green/orange/red)
- [ ] Click "Close" → Return to previous screen

### ✅ Progress Tab
- [ ] Navigate to Progress tab
- [ ] Total tests count displays
- [ ] Average score displays
- [ ] Current streak shows
- [ ] Longest streak shows
- [ ] Swipe to refresh works

### ✅ Exams Tab
- [ ] Navigate to Exams tab
- [ ] Competitive exams list displays
- [ ] Each exam card shows name, description, daily tests
- [ ] Click an exam (should show toast for now)
- [ ] Swipe to refresh works

### ✅ Profile Tab
- [ ] Navigate to Profile tab
- [ ] User name displays correctly
- [ ] Email displays correctly
- [ ] Role badge shows "STUDENT"
- [ ] "Edit Profile" card clickable (shows toast)
- [ ] "Settings" card clickable (shows toast)
- [ ] "About" card clickable (shows toast)
- [ ] Click "Logout" button
- [ ] Confirm logout → Navigate to login screen

### ✅ Navigation
- [ ] Bottom navigation switches between tabs
- [ ] Back button works correctly
- [ ] Navigation state persists
- [ ] No crashes during navigation

---

## API Testing Checklist

### ✅ Network Requests
Open Logcat and filter by `OkHttp`:

- [ ] Login request shows: `POST /auth/login`
- [ ] Authorization header contains Bearer token
- [ ] Subjects request: `GET /subjects`
- [ ] Materials request: `GET /materials/subject/{id}`
- [ ] AI chat request: `POST /ai/chat`
- [ ] Generate test: `POST /tests/generate`
- [ ] Submit test: `POST /tests/submit`
- [ ] Progress: `GET /progress`
- [ ] Exams: `GET /competitive-exams`

### ✅ Error Handling
- [ ] Turn off backend
- [ ] Try to login → Shows error message
- [ ] Try to load subjects → Shows error message
- [ ] Turn on backend
- [ ] Swipe to refresh → Data loads

---

## Edge Cases Testing

### ✅ Empty States
- [ ] Login with account that has no subjects
- [ ] Should show "No subjects available"
- [ ] Navigate to exams with no exams
- [ ] Should show "No competitive exams available"

### ✅ Invalid Input
- [ ] Try login with empty email → Error displayed
- [ ] Try login with invalid email → Error displayed
- [ ] Try login with wrong password → Error message from backend
- [ ] Try registering with existing email → Error message

### ✅ Network Issues
- [ ] Airplane mode ON
- [ ] Try any operation → Error message
- [ ] Airplane mode OFF
- [ ] Retry → Works normally

---

## Performance Checklist

### ✅ UI Responsiveness
- [ ] No ANR (App Not Responding) dialogs
- [ ] Smooth scrolling in lists
- [ ] Quick tab switching
- [ ] Fast activity transitions
- [ ] Loading indicators show for operations > 1 second

### ✅ Memory
- [ ] No memory leaks (check Android Profiler)
- [ ] App size reasonable (~10-15 MB)
- [ ] No excessive memory usage

---

## Admin Testing (Optional)

### ✅ Admin Login
- [ ] Logout from student account
- [ ] Login with: `admin@test.com` / `password123`
- [ ] Redirects to Admin Dashboard
- [ ] Shows "Admin Dashboard - Under Construction" toast

---

## Final Verification

### ✅ Documentation
- [ ] README.md exists and is accurate
- [ ] QUICK_START.md provides clear instructions
- [ ] DEVELOPMENT_STATUS.md shows current state
- [ ] BUILD_CHECKLIST.md covers all testing

### ✅ Code Quality
- [ ] No compilation errors
- [ ] No lint warnings (critical ones)
- [ ] Consistent code style
- [ ] Proper error handling

### ✅ Version Control
- [ ] All files committed to git (if using)
- [ ] .gitignore excludes build files
- [ ] Meaningful commit messages

---

## Known Issues to Accept

1. ✅ **Chat UI:** User and AI messages look identical (acceptable for v1.0)
2. ✅ **Material Viewer:** No PDF/video player (will add in v2.0)
3. ✅ **Admin Dashboard:** Empty placeholder (will implement later)
4. ✅ **Exam Enrollment:** Not implemented yet (planned feature)

---

## Success Criteria

Your build is successful if:
- ✅ App launches without crashes
- ✅ Login works with test accounts
- ✅ All 5 bottom tabs load
- ✅ Subject list displays
- ✅ AI chat sends and receives messages
- ✅ Practice test can be completed
- ✅ Results display correctly
- ✅ Logout works

---

## Troubleshooting Guide

### Issue: "Cannot resolve symbol 'databinding'"
**Solution:** Build → Clean Project → Rebuild Project

### Issue: "Task :app:compileDebugKotlin FAILED"
**Solution:** Check Logcat for specific error, usually missing import

### Issue: "NetworkOnMainThreadException"
**Solution:** Should not occur (we use coroutines), but check repository implementations

### Issue: "401 Unauthorized"
**Solution:** Token expired, logout and login again

### Issue: "Unable to resolve host"
**Solution:** Backend not running or wrong URL in Constants.kt

---

## Next Steps After Testing

1. **If all tests pass:**
   - ✅ App is ready for demo
   - ✅ Can show to stakeholders
   - ✅ Can start adding advanced features

2. **If tests fail:**
   - 📝 Document failures
   - 🔍 Check Logcat for errors
   - 🐛 Fix issues one by one
   - 🔄 Retest after fixes

3. **Enhancements to consider:**
   - 🎨 Improve chat UI differentiation
   - 📱 Add PDF viewer library
   - 🔔 Implement push notifications
   - 💾 Add offline mode with Room
   - 👨‍💼 Complete admin dashboard

---

## Build Statistics

**Expected Results:**
- Build time: ~30-60 seconds
- APK size: ~10-15 MB
- Install time: ~10-20 seconds
- First launch: ~2-3 seconds

---

## Final Checklist Summary

- [ ] Backend running ✅
- [ ] App builds successfully ✅
- [ ] App installs on device/emulator ✅
- [ ] Login works ✅
- [ ] All tabs functional ✅
- [ ] AI chat works ✅
- [ ] Tests work ✅
- [ ] No critical crashes ✅

---

**If all boxes are checked, congratulations! 🎉**
**Your Campus Helper 2 app is ready!**

---

**Build Date:** December 2024  
**Version:** 1.0.0-beta  
**Status:** Ready for Testing ✅
